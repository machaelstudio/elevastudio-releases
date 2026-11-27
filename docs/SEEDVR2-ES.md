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

1. **Instala ComfyUI y ábrelo.** Lo más sencillo es la aplicación oficial de
   [comfy.org/download](https://www.comfy.org/download) (Windows y Mac). También sirve la versión
   portable para Windows; mira "Versión portable" más abajo.
2. **Instala el primer complemento desde ComfyUI.** Abre **Manage Extensions**: el ícono de
   pieza de rompecabezas en la barra superior, o **Help → Manage Extensions**. Busca `SeedVR2`
   e instala **ComfyUI-SeedVR2_VideoUpscaler** (de *numz* / AInVFX).
3. **Agrega el segundo complemento a mano.** *SeedVR2 Tiling Upscaler* (de *moonwhaler*) no
   está en esa lista, así que no aparece en la búsqueda:
   1. Descárgalo como zip: [comfyui-seedvr2-tilingupscaler](https://github.com/moonwhaler/comfyui-seedvr2-tilingupscaler/archive/refs/heads/main.zip).
   2. Descomprímelo dentro de la carpeta `custom_nodes` de ComfyUI. Con la aplicación de
      escritorio es `Documentos/ComfyUI/custom_nodes`; con la versión portable es
      `ComfyUI_windows_portable\ComfyUI\custom_nodes`.
   3. Revisa el resultado: `custom_nodes/comfyui-seedvr2-tilingupscaler-main/` debe contener
      directamente los archivos del complemento (`__init__.py`, `upscaler.py`, …), no otra
      carpeta con el mismo nombre.
   4. Reinicia ComfyUI.
4. **Deja ComfyUI abierto.** En Eleva Studio abre **Restaurar** y pulsa **Comprobar de nuevo**.
   Los pasos se marcan uno por uno, así se ve qué parte falta, y después aparece
   "Listo · conectado a ComfyUI".

Eleva Studio encuentra ComfyUI por sí solo en las direcciones habituales
(`http://127.0.0.1:8188`, y `http://127.0.0.1:8000` para la aplicación de escritorio). Solo si
cambiaste el puerto hay que escribir la dirección en "Dirección de ComfyUI (avanzado)".

Las versiones recientes de ComfyUI traen también sus propios flujos de SeedVR2. Son cosa aparte:
Eleva Studio usa los dos complementos de arriba, porque el de mosaicos es el que permite que los
tamaños grandes de impresión quepan en la memoria.

### Versión portable: activar Manage Extensions

En la versión portable el gestor de extensiones está apagado hasta que lo actives una vez:

1. Abre la carpeta `ComfyUI_windows_portable`, escribe `cmd` en la barra de direcciones y pulsa
   Enter.
2. Ejecuta `.\python_embeded\python.exe -m pip install -r ComfyUI\manager_requirements.txt`
   (si ese archivo no existe, ejecuta antes `update\update_comfyui.bat`).
3. Haz una copia de `run_nvidia_gpu.bat`, ábrela con el Bloc de notas y agrega
   ` --enable-manager` al final de la línea que empieza con `.\python_embeded\python.exe`.
4. Desde ahora abre ComfyUI con esa copia.

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
- **Dice que falta un complemento que ya instalaste**: reinicia ComfyUI; los complementos solo
  se cargan al abrirlo. Si sigue faltando *SeedVR2 Tiling Upscaler*, abre su carpeta dentro de
  `custom_nodes` y revisa que los archivos no hayan quedado una carpeta más adentro (paso 3).
- **No encuentras el Manager**: ahora se llama **Manage Extensions** (ícono de pieza de
  rompecabezas o menú Help). En la versión portable hay que activarlo primero, mira arriba.
- **Sigue sin memoria después del reintento**: elige un modelo `Q4_K_M` GGUF o un tamaño de
  salida menor.
