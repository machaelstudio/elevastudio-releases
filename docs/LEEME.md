# Eleva Studio — guía de uso

Recorte y ampliación de fotos en tu propia computadora. No sube nada a internet y no tiene
suscripción. El programa está en inglés; para ponerlo en español abre **Ajustes** (el engranaje
abajo a la izquierda) → **Language** → **Español**.

## Instalar

Descarga la última versión en
[github.com/machaelstudio/elevastudio-releases/releases/latest](https://github.com/machaelstudio/elevastudio-releases/releases/latest):

- **Windows 10 / 11 (64 bits)**: abre `ElevaStudio-<versión>-windows-x64-setup.exe`. El instalador
  está firmado, así que Windows y Smart App Control lo dejan pasar sin avisos. No necesita permisos
  de administrador.
- **Mac (Apple Silicon, macOS 14 o más nuevo)**: abre `ElevaStudio-<versión>-macos-arm64.dmg` y
  arrastra Eleva Studio a Aplicaciones. La app está firmada y notarizada por Apple.

Cuando hay una versión nueva, el programa te avisa al abrirlo y se actualiza solo.

## Herramientas

- **Recortar** (quitar fondo): cuatro calidades (Rápido, Preciso, Máxima, Personas) y la opción
  **Bordes finos** para pelo y peluche. Luego elige el fondo nuevo: transparente, un color, tu
  propia imagen o la foto desenfocada, con sombra suave y margen opcionales.
- **Ampliar**: 2×, 3× o 4×, en modo Foto o Logo / arte. Pensado para imprimir en gran formato.
- **Restaurar**: la ampliación y restauración de máxima calidad (SeedVR2). Necesita una
  instalación de dos pasos, una sola vez: instalar ComfyUI, un programa gratuito, y pulsar
  Descargar en el panel Restaurar; mira la [guía de instalación](SEEDVR2-ES.md). Todo lo demás
  funciona sin eso.
- **Vectorizar**: convierte un logo, letras o una ilustración de colores planos en formas que se
  mantienen nítidas a cualquier tamaño y las guarda como SVG, que abre en CorelDRAW,
  Illustrator, Inkscape y programas de corte. Elige **Color** (pocos, algunos o muchos colores) o
  **Un color** (las partes oscuras como formas negras) y cuánto detalle conservar. Para un fondo
  transparente usa Recortar primero; para un logo pequeño o pixelado usa antes Ampliar (Logo /
  arte). Con un ancho de impresión puesto en Exportar, el SVG abre a ese tamaño.
- **Por lotes**: abre varias fotos y activa "Aplicar a todas las imágenes".
- Comparador antes / después, deshacer (Ctrl+Z), guardar (Ctrl+S), abrir (Ctrl+O).
- **Zoom y movimiento de la vista previa**: pellizca en el trackpad o gira la rueda del mouse
  para acercar el punto bajo el cursor, arrastra la imagen (o mueve dos dedos) para recorrerla y
  haz doble clic para verla al 100% (píxeles reales) y volver. La línea de comparación se mueve
  con su círculo.

La primera vez que usas cada herramienta se descarga un componente (necesitas internet solo en ese
momento): unos 170 MB para Recortar (930 MB en Máxima) y 34 MB para Ampliar. En Ajustes ves cuánto
ocupa y puedes abrir la carpeta.

## Exportar para impresión y DTF

En la tarjeta **Exportar** hay un selector de **Uso**:

- **Pantalla**: PNG o JPG normal, sin etiqueta de resolución.
- **Impresión**: los archivos llevan etiqueta de resolución (300 ppp por defecto; de 150 a 600),
  así CorelDRAW, Illustrator y Photoshop los abren al tamaño físico correcto. El TIFF es de 8 bits,
  LZW (sin pérdida), con transparencia si la hay.
- **Transfer DTF**: PNG con transparencia más la limpieza que piden los RIP de DTF, porque el RIP
  imprime tinta blanca bajo cada píxel que no sea totalmente transparente:
  - **Bordes sólidos**: sin píxeles semitransparentes (si no, los bordes suaves salen con un filo blanco).
  - **Quitar puntos sueltos**: puntitos aislados que deja el recorte y que saldrían como puntos blancos.
  - **Encoger bordes 1 px**: retrae el arte un píxel para que la base blanca nunca asome.
  - **Recortar márgenes transparentes**: deja solo el arte, útil para armar planchas.
  - **Espejar horizontalmente**: apagado por defecto. La mayoría de los RIP espejan solos; actívalo
    solo si el tuyo no lo hace.

**Tamaño y destino del archivo**: debajo del formato ves el tamaño del archivo que se va a escribir
("Tamaño: 12.4 MB · 4800 × 3600 px") y dónde se guarda. En Ajustes → **Guardar en** eliges entre
preguntar cada vez, la carpeta de la foto original, o una carpeta fija; nunca se sobrescribe nada
(se añade -2, -3).

**Ancho de impresión**: escribe el ancho final (pulgadas o cm) y el aviso te dice la resolución que
alcanza la imagen a ese tamaño. Si queda por debajo del objetivo, un clic la amplía con la escala
necesaria (hasta 4×). Ejemplo: una foto de 1200 px impresa a 12 in de ancho da 100 ppp; "Ampliar 3×"
la lleva a 300 ppp.

## Tarjeta gráfica

El programa usa la tarjeta gráfica cuando puede: DirectML en Windows (casi cualquier GPU NVIDIA,
AMD o Intel de los últimos años) y CoreML en Mac. Arriba a la derecha dice qué está usando, por
ejemplo "Listo · GPU (DirectML)". Si dice "CPU", todo funciona igual, solo más lento.

## Límites y consejos

- El tamaño máximo del resultado al ampliar es 16 000 px por lado. Para fotos muy grandes usa 2×.
- En casos difíciles (pelo suelto, vidrio, joyas) usa Máxima con Bordes finos.
- Para transparencia usa PNG o TIFF; el JPG se aplana sobre blanco.
- JPG sirve para pantalla y fotos; para transfers usa siempre PNG.
