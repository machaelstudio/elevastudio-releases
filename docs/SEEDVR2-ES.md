# Restaurar (máxima calidad) — guía de instalación

La herramienta **Restaurar** amplía y restaura fotos pixeladas o de baja calidad con SeedVR2, un
modelo de restauración demasiado grande para venir dentro de Eleva Studio (de 3 a 15 GB por
modelo y una tarjeta gráfica con 8 GB de memoria o más). Por eso Eleva Studio usa una instalación
de ComfyUI en la misma computadora y la maneja por ti: tú sigues trabajando en Eleva Studio y
ComfyUI solo tiene que estar abierto.

Es la única herramienta que necesita instalación. Todo lo demás de Eleva Studio funciona sin
esto. Si solo quieres ampliar o mejorar una imagen, la herramienta **Ampliar** lo hace al momento.

## Qué necesitas

- **Windows**: una tarjeta gráfica NVIDIA con 8 GB de memoria o más (12 GB o más recomendado) y
  unos 20 GB libres en disco.
- **Mac**: Apple Silicon con 32 GB de memoria o más. Funciona, pero tarda varios minutos por foto.
- Internet para las descargas, que se hacen una sola vez.

## Instalación (unos 15 minutos, una sola vez)

1. **Instala ComfyUI.** Lo más sencillo es la aplicación oficial de
   [comfy.org/download](https://www.comfy.org/download) (Windows y Mac).
2. **Abre ComfyUI** y abre el **Manager** (el botón con una pieza de rompecabezas). Elige
   **Custom Nodes Manager**, busca e instala:
   - **ComfyUI-SeedVR2_VideoUpscaler** de *numz* (elige la versión **nightly** si pregunta).
   - **SeedVR2 Tiling Upscaler** de *moonwhaler* (`comfyui-seedvr2-tilingupscaler`).
   Reinicia ComfyUI cuando el Manager lo pida.
3. **Deja ComfyUI abierto.**
4. En Eleva Studio abre **Restaurar** y pulsa **Comprobar de nuevo**. Los pasos se marcan como
   hechos y aparece "Listo · conectado a ComfyUI".

Los modelos **no** se descargan durante la instalación: la primera vez que pulses **Restaurar
imagen**, ComfyUI descarga el elegido (el progreso se ve en la ventana de ComfyUI). Después ya
queda en la computadora.

## Cómo usarlo

- **Calidad** muestra los modelos SeedVR2 que conoce ComfyUI:
  - Modelos *3b*: más rápidos, suficientes para casi todas las fotos. `fp8` necesita unos 8 GB de
    memoria gráfica; `Q4` GGUF, menos.
  - Modelos *7b*: el mejor detalle, más lentos, 16 GB de memoria gráfica o más.
- **Tamaño de salida**: 2×, 3×, 4× o **Impresión**, que calcula los píxeles que necesita tu ancho
  de impresión a los ppp elegidos (el ancho se pone en Exportar).
- Pulsa **Restaurar imagen**. Una foto de 1200 px a 4× tarda alrededor de un minuto en una RTX
  3060. Si ComfyUI se queda sin memoria, Eleva Studio reintenta una vez en un modo de poca
  memoria, más lento pero que normalmente termina.
- El resultado es un paso normal: puedes deshacerlo, quitarle el fondo y exportarlo con las
  opciones de impresión o DTF como cualquier otra imagen.

## Problemas

- **"No se encontró ComfyUI en esta computadora"**: abre ComfyUI, espera a que cargue su ventana
  y pulsa Comprobar de nuevo. Si cambiaste el puerto de ComfyUI, escribe la dirección nueva en
  "Dirección de ComfyUI (avanzado)".
- **"faltan los dos complementos SeedVR2"**: termina el paso 2 y reinicia ComfyUI.
- **Sigue sin memoria después del reintento**: elige un modelo `Q4_K_M` GGUF o un tamaño de
  salida menor.
