# Restaurar (máxima calidad) — guía de instalación

La herramienta **Restaurar** amplía y restaura fotos pixeladas o de baja calidad con SeedVR2, un
modelo de restauración demasiado grande para venir dentro de Eleva Studio (de 3 a 8 GB, y
necesita una tarjeta gráfica con 8 GB de memoria o más). Por eso Eleva Studio usa ComfyUI, un
programa gratuito aparte en la misma computadora, y lo maneja por ti: sigues trabajando en Eleva
Studio y ComfyUI solo tiene que estar abierto de fondo.

Es la única herramienta que necesita instalación. Todo lo demás de Eleva Studio funciona sin
instalar nada.

## Qué necesitas

- **Windows**: una tarjeta gráfica NVIDIA con 8 GB de VRAM o más (12 GB o más recomendado) y
  unos 20 GB libres en disco.
- **Mac**: Apple Silicon con 32 GB o más de memoria unificada. Funciona, pero cada foto tarda
  varios minutos.
- Internet para las descargas, que se hacen una sola vez.

## Instalación: dos pasos

1. **Instala ComfyUI y déjalo abierto.** En Eleva Studio abre **Restaurar** y pulsa
   **Obtener ComfyUI**; se abre [comfy.org/download](https://www.comfy.org/download). Instala
   la aplicación de escritorio como cualquier otro programa (Windows y Mac), ábrela y deja que
   termine su primer arranque. No hay que hacer nada dentro de ComfyUI.
2. **Pulsa Descargar en Eleva Studio.** De vuelta en **Restaurar**, pulsa **Comprobar de
   nuevo**: el paso 1 queda marcado y el botón ahora dice **Descargar (3.9 GB)**. Púlsalo.
   Eleva Studio descarga el componente de Restaurar y lo coloca por sí mismo en la carpeta
   correcta de ComfyUI. Cuando la barra termina, el panel muestra "Listo · conectado a ComfyUI".

Eso es todo: no hay nada que buscar, descomprimir ni instalar dentro de ComfyUI, y no hace falta
reiniciarlo.

Conviene saber:

- La descarga se puede detener con **Detener** y continuar después; sigue donde quedó. Lo mismo
  ocurre por sí solo si se corta la conexión.
- Los archivos se comprueban después de la descarga, así que nunca se usa una descarga dañada.
- Eleva Studio encuentra ComfyUI por sí mismo en las direcciones habituales
  (`http://127.0.0.1:8000` para la aplicación de escritorio, `http://127.0.0.1:8188` para la
  versión portable). Solo si cambiaste el puerto tienes que escribir la dirección en "Dirección
  de ComfyUI (avanzado)".
- ComfyUI debe ser la versión 0.28 o posterior (julio de 2026). Las anteriores no incluyen
  SeedVR2; actualiza ComfyUI y pulsa **Comprobar de nuevo**.

## Cómo usarlo

- **Calidad**:
  - *Estándar*: rápida y suficiente para la mayoría de las fotos. Es la que descarga la
    instalación.
  - *Alto detalle*: el mayor detalle; más lenta, y pide una tarjeta gráfica con 16 GB o más.
    Elígela en la lista y el botón pasa a ser **Descargar esta calidad (8.2 GB)**; después es
    una opción más de la lista.
- **Tamaño de salida**: 2×, 3×, 4× o **Impresión**, que calcula los píxeles que necesita tu
  ancho de impresión a los dpi elegidos (el ancho se pone en la tarjeta Exportar).
- Pulsa **Restaurar imagen**. Los resultados grandes se trabajan por partes, así que el avance
  va subiendo; una foto de 1200 px a 4× tarda unos minutos en una RTX 3060, más en tarjetas
  menores. Si ComfyUI se queda sin memoria gráfica, Eleva Studio reintenta una vez en modo de
  poca memoria (partes más pequeñas), más lento pero normalmente funciona.
- El resultado es un paso normal del historial: puedes deshacerlo, quitar el fondo, elegir un
  fondo y exportarlo con las opciones de DTF o impresión como cualquier otra imagen.

## Problemas

- **"No se encontró ComfyUI en esta computadora"**: abre ComfyUI, espera a que cargue su
  ventana y pulsa **Comprobar de nuevo**. Si cambiaste el puerto de ComfyUI, escribe la nueva
  dirección en "Dirección de ComfyUI (avanzado)".
- **"Este ComfyUI es demasiado antiguo para Restaurar"**: actualiza ComfyUI (en la aplicación
  de escritorio: Help → Check for updates), reinícialo y pulsa **Comprobar de nuevo**.
- **La descarga se detiene o falla**: pulsa **Descargar** otra vez; continúa donde quedó. Si
  sigue fallando, revisa el espacio libre en disco.
- **"El componente ya está en su lugar, pero ComfyUI todavía no lo muestra"**: reinicia ComfyUI
  y pulsa **Comprobar de nuevo**.
- **Sigue faltando memoria después del reintento**: usa la calidad *Estándar* o un tamaño de
  salida menor, y cierra otros programas que usen la tarjeta gráfica.

## Otras instalaciones

- **ComfyUI en otra computadora.** Eleva Studio puede usar un ComfyUI de tu red (escribe su
  dirección en "Dirección de ComfyUI (avanzado)"), pero no puede descargar dentro de él. Pon tú
  mismo estos archivos de [Comfy-Org/SeedVR2](https://huggingface.co/Comfy-Org/SeedVR2):
  `seedvr2_3b_fp8_e4m3fn.safetensors` en `ComfyUI/models/diffusion_models` y
  `seedvr2_ema_vae_fp16.safetensors` en `ComfyUI/models/vae`.
- **Ya tienes archivos de SeedVR2.** Cualquier modelo SeedVR2 que esté en
  `models/diffusion_models` aparece en la lista de Calidad con su propio nombre, siempre que el
  archivo VAE de arriba esté en `models/vae`.
- **Instalaciones hechas para una versión anterior de Eleva Studio** (los complementos
  *ComfyUI-SeedVR2_VideoUpscaler* y *SeedVR2 Tiling Upscaler*) siguen funcionando como antes.
  Para pasar a la vía integrada, elige *Estándar · descargar* en la lista de Calidad y pulsa el
  botón; después los complementos dejan de hacer falta.
