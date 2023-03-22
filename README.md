<!--
arguelles v2.2.0
author: Michele Piazzai
contact: michele.piazzai@uc3m.es
license: MIT
-->

# arguelles

Argüelles is a beamer theme that helps you create beautiful presentations. It aims for simplicity and readability by following best practices of graphic design. The layout is elegant but subtle, so as to keep the audience's attention on your content. This is brought to life by Alegreya, one of the 53 Fonts of the Decade selected by the Association Typographique Internationale (2011).

The theme requires the packages [Alegreya/AlegreyaSans](https://ctan.org/pkg/alegreya), [eulervm](https://ctan.org/pkg/eulervm), [mathalpha](https://www.ctan.org/pkg/mathalpha), [microtype](https://ctan.org/pkg/microtype), [fontawesome5](https://ctan.org/pkg/fontawesome5), [opencolor](https://www.ctan.org/pkg/opencolor), [enumitem](https://www.ctan.org/pkg/enumitem), [parskip](https://www.ctan.org/pkg/parskip), and [tikz/pgf](https://ctan.org/pkg/pgf) to be installed on your computer. These are included in common LaTeX distributions, such as [MiKTeX](https://ctan.org/pkg/miktex) and [TeXLive](https://ctan.org/pkg/texlive).

## Demo

The files `demo.tex` and `demo.pdf` demonstrate the main features of the theme.

### Serif

![](https://github.com/piazzai/arguelles/blob/master/demo/demo-arguelles-serif.gif)

### Sans-serif

![](https://github.com/piazzai/arguelles/blob/master/demo/demo-arguelles-sans.gif)

## Installation

Argüelles is hosted on CTAN and distributed as part of MikTex and TeXLive. It can also be installed manually by cloning this repository in your `$HOME/texmf/tex/latex` folder, which is automatically searched by LaTeX. If you do not have this folder, you can [create one](https://www.ias.edu/math/computing/faq/local-latex-style-files).

## Usage

By default, the theme uses serif fonts for body text. Loading it with the `sans` option makes sans-serif fonts default, keeping serif only for math type. Because sans-serif font is more space-efficient, this could be useful for slides that contain more text and bullet points. See the two animations below for comparison.

The `frameno` option adds frame numbering in the bottom right corner of each frame. By default, frame numbers are hidden on title and plain frames. They can also be suppressed on individual frames by `\begin{frame}[noframenumbering]`.

The `splitnav` option makes the navigation bar in the headline display only the current section and its frames. This could be preferable if your presentation has only a few sections, which do not adequately fill the headline, or if it has a lot of sections and the headline looks too crowded.

The `mp` option loads additional dependencies that could be useful for designing scientific presentations. These currently include [ulem](https://ctan.org/pkg/ulem), [booktabs](https://ctan.org/pkg/booktabs), [dcolumn](https://ctan.org/pkg/dcolumn), [makecell](https://ctan.org/pkg/makecell), [colortbl](https://www.ctan.org/pkg/colortbl), [cancel](https://www.ctan.org/pkg/cancel), [pgfplots](https://www.ctan.org/pkg/pgfplots), and [csvsimple](https://www.ctan.org/pkg/csvsimple). In addition, the option loads the [calc](https://tikz.dev/library-calc) library for TikZ, and the [statistics](https://tikz.dev/pgfplots/libs-statistics) and [fillbetween](https://tikz.dev/pgfplots/libs-fillbetween) libraries for PGFplots.

## Customization

It is possible to change parts of the theme by altering the style files. There are five such files:

-   `beamercolortheme*.sty` sets the colors;
-   `beamerfonttheme*.sty` sets font styles and weights;
-   `beamerinnertheme*.sty` sets the appearance of frames;
-   `beameroutertheme*.sty` sets the appearance of headline and frame titles;
-   `beamertheme*.sty` loads required packages, and defines custom colors and commands.

### Colors

The theme ships with the `opencolor` package, which provides color definitions for the [Open Color](https://yeun.github.io/open-color/) library. By default, the background is set to `oc-gray-0`. The foreground and body text are set to `oc-gray-9`. The color of accented text is `oc-red-9`.

These settings are provided in `beamercolortheme*.sty` and can be customized using any default or opencolor name. For example:

```tex
\setbeamercolor*{structure}{bg=oc-blue-0,fg=black!80}
```

See the opencolor documentation for additional details.

### Font weights

Alegreya is a comprehensive family and comes with a variety of weights, as does its sister family Alegreya Sans. In addition to the usual bold provided by `\bfseries`, Alegreya comes in medium, extra bold, and black. Alegreya Sans further comes in light and thin. These weights are set by commands like `\AlegreyaExtraBold` or `\AlegreyaSansThin`, as explained in the Alegreya documentation, and can be combined with `\scshape` or `\itshape` to produce a variety of effects.

The file `beamerfonttheme*.sty` sets the type for various elements of the layout. For example, the appearance of frame titles is determined by the command:

```tex
\setbeamerfont{frame title}{size=\Large}
```

If you wanted to give frame titles a little bit more weight, you could write `series=\AlegreyaMedium` and `size=\Large`. If you wanted to make them slightly larger, you could write `size=\LARGE`.

By default, the theme uses serif type for body text and reserves sans-serif type for the presentation title, formatted in black weight. It is possible to modify this behavior by rewriting parts of `beamerfonttheme*.sty`. For example, the appearance of the presentation title is determined by:

```tex
\setbeamerfont{title}{series=\AlegreyaSansBlack,size=\LARGE}
```

Changing `\AlegreyaSansBlack` to `\AlegreyaBlack` in this line sets the title to serif, keeping the same weight. Deleting `\usefonttheme{serif}` near the top of the file makes sans-serif type the new default for all text. Changing `\urlstyle{same}` to `\urlstyle{sf}` makes URLs sans-serif, and deleting the line altogether resets them to true type.

### Figures

Figures are automatically set to old style, which is more varied and dynamic than the lining ("modern") style. If you wish to use lining figures instead, you can set these as default by opening `beamertheme*.sty` and removing the `osf` options from the packages `Alegreya` and `AlegreyaSans`.

Both old-style and lining figures are also available in a monospaced version, which is helpful for tables and other environments where numbers are displayed in column. It is possible to use monospaced versions locally with `\AlegreyaTOsF` (for old style) and `\AlegreyaTLF` (for lining). They can also be set as global defaults by loading packages with the `tf` option, as in:

```tex
\RequirePackage[osf,tf]{Alegreya}
\RequirePackage[osf,tf]{AlegreyaSans}
```

## Known issues

Argüelles is built with the intention to reserve as much space as possible for the content of your slides. When using subsections, the progress bar in the headline places dots on multiple lines, which takes space away from your content. The theme does not handle this situation well. You can force the dots to appear on the same line by loading beamer with the `compress` option, as in the demo:

```tex
\documentclass[compress]{beamer}
```

If you find any other problem using this package, please [open an issue](https://github.com/piazzai/arguelles/issues).
