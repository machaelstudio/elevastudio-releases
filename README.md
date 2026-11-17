# Eleva Studio — descargas

Aquí se publican las versiones de **Eleva Studio**, el editor de fotos con IA (quitar fondo y mejorar resolución) que corre en tu propia computadora, gratis y sin subir nada a internet.

## Descargar

Entra a la última versión en [Releases](https://github.com/machaelstudio/elevastudio-releases/releases/latest):

- **Windows (10/11, 64 bits)**: `ElevaStudio-<versión>-windows-x64-setup.exe`. Instalador firmado; no necesita permisos de administrador.
- **Mac (Apple Silicon, macOS 14 o más nuevo)**: `ElevaStudio-<versión>-macos-arm64.dmg`. Firmado y notarizado por Apple.

La primera vez que uses cada herramienta, el programa descarga su modelo de IA (170 MB para quitar fondo, 65 MB para mejorar; 930 MB para "máxima calidad"). Después funciona sin internet.

El programa se actualiza solo: cuando hay una versión nueva te avisa al abrirlo.

## Modelos

La release [`models-1`](https://github.com/machaelstudio/elevastudio-releases/releases/tag/models-1) contiene los modelos ONNX que el programa descarga: U²-Net, IS-Net y BiRefNet (quitar fondo, del proyecto [rembg](https://github.com/danielgatis/rembg)) y Real-ESRGAN x2plus / x4plus / x4plus-anime (mejorar, de [xinntao/Real-ESRGAN](https://github.com/xinntao/Real-ESRGAN), exportados a ONNX). Todos tienen licencias abiertas que permiten el uso comercial.

El código fuente está en [machaelstudio/elevastudio](https://github.com/machaelstudio/elevastudio).
