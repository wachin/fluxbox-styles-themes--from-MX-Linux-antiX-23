# Fluxbox styles and themes from MX Linux / antiX 23

Spanish documentation is available here: [README_ES.md](README_ES.md).

This repository is a curated collection of Fluxbox styles gathered from MX Linux and antiX 23, prepared so they can be installed directly into a user's Fluxbox styles directory.

The goal is to keep the themes usable, portable, and easy for other developers to inspect or adapt.

## Repository layout

```text
styles/
  FT10dark
  MX-Nyz
  MX-debian-blue
  MX-debian-blue-rounded
  <theme-directory>/theme.cfg
  <theme-directory>/pixmaps/
```

Fluxbox supports both layouts used here:

- A style as a single file directly under `styles/`.
- A style as a directory containing `theme.cfg` and optional assets such as `pixmaps/`.

## Included theme families

- `FT10dark`
- `LemonSpacePro2`: Huge, Large, Medium, Small
- `MX-Nyz`
- `MX-Squared`: blue, blue2, green variants in Medium and Small sizes
- `MX-comfort`: light and dark variants in Medium and Small sizes
- `MX-debian-blue`
- `MX-debian-blue-rounded`
- `Numix`: Huge, Large, Medium, Small
- `PrettyPink`: Huge, Large, Medium, Small
- `niroki`: Medium and Small
- `sleek2antiX`: Huge, Large, Medium, Small
- `sleek2flux`: Huge, Large, Medium, Small

## Installation

Clone or download this repository. Then copy the styles folder into your Fluxbox configuration:

```bash
mkdir -p ~/.fluxbox/styles
cp -a styles/* ~/.fluxbox/styles/
```

Then open the Fluxbox menu and select:

```text
Styles
```

If Fluxbox does not refresh the menu immediately, run:

```bash
fluxbox-remote reconfig
```

or restart Fluxbox from the menu.

## Development notes

When editing these themes, keep them self-contained whenever possible:

- Prefer relative pixmap names that resolve inside the theme directory or its `pixmaps/` subdirectory.
- Avoid absolute wallpaper or pixmap paths such as `/usr/share/...` unless the dependency is intentional and documented.
- Preserve upstream author and license comments inside theme files.
- Keep size variants grouped by family and use consistent suffixes such as `Small`, `Medium`, `Large`, and `Huge`.

## Validation

The current tree was checked for active `*.pixmap` references that point to missing files. The validation expects pixmaps to exist either next to the style file or inside a sibling `pixmaps/` directory.

Known portability fixes applied here:

- `niroki-medium` and `niroki-small` referenced a missing `toolbar_focused.xpm`; they now use the shipped `toolbar.xpm`.
- `MX-Squared_green-Medium` and `MX-Squared_green-Small` referenced `/usr/share/images/fluxbox/fluxbox.png`; they now use a solid fallback background.
- `MX-debian-blue-rounded` had malformed quoted background lines and referenced a Debian wallpaper not included in this repository; it now uses a solid fallback background.

## Optional compositor

These themes work without a compositor, but window shadows can make Fluxbox windows easier to distinguish. A lightweight Picom command that keeps windows fully opaque while adding shadows is:

```bash
picom --backend xrender --shadow --shadow-radius 17 --shadow-offset-x -17 --shadow-offset-y -17 --shadow-opacity 0.30 --inactive-opacity 1 --active-opacity 1 --frame-opacity 1 --no-fading-openclose &
```

Add it to `~/.fluxbox/startup` before `exec fluxbox` if you want it enabled at login.

## License

The themes come from different upstream sources and may carry their own license comments inside the individual style files. Check the relevant theme file before redistributing or modifying a specific style.
