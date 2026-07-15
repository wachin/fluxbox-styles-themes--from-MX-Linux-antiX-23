# Estilos y temas de Fluxbox de MX Linux / antiX 23

Este repositorio es una colección organizada de estilos de Fluxbox reunidos desde MX Linux y antiX 23, preparados para que se puedan instalar directamente en la carpeta de estilos de Fluxbox del usuario.

El objetivo es mantener los temas usables, portables y fáciles de revisar o adaptar por otros desarrolladores.

## Estructura del repositorio

```text
styles/
  FT10dark
  MX-Nyz
  MX-debian-blue
  MX-debian-blue-rounded
  <directorio-del-tema>/theme.cfg
  <directorio-del-tema>/pixmaps/
```

Fluxbox soporta los dos formatos usados aquí:

- Un estilo como archivo individual directamente dentro de `styles/`.
- Un estilo como directorio que contiene `theme.cfg` y recursos opcionales como `pixmaps/`.

## Familias de temas incluidas

- `FT10dark`
- `LemonSpacePro2`: Huge, Large, Medium, Small
- `MX-Nyz`
- `MX-Squared`: variantes blue, blue2 y green en tamaños Medium y Small
- `MX-comfort`: variantes claras y oscuras en tamaños Medium y Small
- `MX-debian-blue`
- `MX-debian-blue-rounded`
- `Numix`: Huge, Large, Medium, Small
- `PrettyPink`: Huge, Large, Medium, Small
- `niroki`: Medium y Small
- `sleek2antiX`: Huge, Large, Medium, Small
- `sleek2flux`: Huge, Large, Medium, Small

## Instalación

Clone o descargue este repositorio. Luego copie la carpeta de estilos dentro de su configuración de Fluxbox:

```bash
mkdir -p ~/.fluxbox/styles
cp -a styles/* ~/.fluxbox/styles/
```

Después abra el menú de Fluxbox y seleccione:

```text
Styles
```

Si Fluxbox no actualiza el menú inmediatamente, ejecute:

```bash
fluxbox-remote reconfig
```

o reinicie Fluxbox desde el menú.

## Notas para desarrollo

Cuando edite estos temas, manténgalos autocontenidos siempre que sea posible:

- Prefiera nombres relativos de pixmaps que se resuelvan dentro del directorio del tema o dentro de su subdirectorio `pixmaps/`.
- Evite rutas absolutas de wallpapers o pixmaps como `/usr/share/...`, salvo que esa dependencia sea intencional y esté documentada.
- Conserve los comentarios de autor y licencia originales dentro de los archivos de tema.
- Mantenga las variantes de tamaño agrupadas por familia y use sufijos consistentes como `Small`, `Medium`, `Large` y `Huge`.

## Validación

El árbol actual fue revisado buscando referencias activas a `*.pixmap` que apunten a archivos inexistentes. La validación espera que los pixmaps existan junto al archivo de estilo o dentro de un directorio hermano llamado `pixmaps/`.

Correcciones de portabilidad aplicadas aquí:

- `niroki-medium` y `niroki-small` referenciaban un archivo inexistente llamado `toolbar_focused.xpm`; ahora usan el archivo incluido `toolbar.xpm`.
- `MX-Squared_green-Medium` y `MX-Squared_green-Small` referenciaban `/usr/share/images/fluxbox/fluxbox.png`; ahora usan un fondo sólido de respaldo.
- `MX-debian-blue-rounded` tenía líneas de fondo mal formadas con comillas y referenciaba un wallpaper de Debian no incluido en este repositorio; ahora usa un fondo sólido de respaldo.

## Compositor opcional

Estos temas funcionan sin compositor, pero las sombras de ventana pueden hacer que las ventanas de Fluxbox sean más fáciles de distinguir. Un comando liviano de Picom que mantiene las ventanas totalmente opacas y añade sombras es:

```bash
picom --backend xrender --shadow --shadow-radius 17 --shadow-offset-x -17 --shadow-offset-y -17 --shadow-opacity 0.30 --inactive-opacity 1 --active-opacity 1 --frame-opacity 1 --no-fading-openclose &
```

Añádalo a `~/.fluxbox/startup` antes de `exec fluxbox` si quiere activarlo al iniciar sesión.

## Licencia

Los temas vienen de diferentes fuentes originales y pueden tener sus propios comentarios de licencia dentro de cada archivo de estilo. Revise el archivo del tema correspondiente antes de redistribuir o modificar un estilo específico.
