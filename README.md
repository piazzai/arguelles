<!--
- arguelles v1.2.0
- Copyright (c) 2020 Michele Piazzai. Contact: michele.piazzai@uc3m.es
- This work is released under the MIT License and is free to use, copy, modify,
- merge, publish, distribute, sublicense, and/or sell. See LICENSE for details.
-->

# Argüelles

Argüelles is a beamer theme that helps you create beautiful presentations. It aims for simplicity and readability by following best practices of graphic design. The layout is elegant but subtle, so as to keep the audience's attention on your content. This is brought to life by Alegreya, one of the 53 Fonts of the Decade selected by the Association Typographique Internationale (2011).

The theme requires the packages [tikz](https://ctan.org/pkg/pgf), [microtype](https://ctan.org/pkg/microtype), [makecell](https://ctan.org/pkg/makecell), [Alegreya](https://ctan.org/pkg/alegreya), [cancel](https://ctan.org/pkg/cancel), [euler](https://ctan.org/pkg/euler), and [fontawesome5](https://ctan.org/pkg/fontawesome5) to be installed on your computer. These are included in most LaTeX distributions, such as [MiKTeX](https://ctan.org/pkg/miktex) and [TeXLive](https://ctan.org/pkg/texlive).

## Demo

The files `demo.tex` and `demo.pdf` demonstrate the main features of the theme.

![](https://github.com/piazzai/arguelles/blob/master/demo/demo-arguelles.gif)

## Installation

Argüelles is [hosted on CTAN](https://ctan.org/pkg/beamertheme-arguelles) and available as part of TeXLive. It can also be installed manually by cloning this repository in your `$HOME/texmf/tex/latex` folder, which is automatically searched by LaTeX. If you do not have this folder, you can [create one](https://www.ias.edu/math/computing/faq/local-latex-style-files).

## Customization

It is possible to change parts of the theme by altering the style files. There are five such files:

-   `beamercolortheme*.sty` sets the colors;
-   `beamerfonttheme*.sty` sets font styles and weights;
-   `beamerinnertheme*.sty` sets the appearance of frames;
-   `beameroutertheme*.sty` sets the appearance of headline and frame titles;
-   `beamertheme*.sty` loads required packages, and defines custom colors and commands.

### Colors

Suppose you want to change the color scheme. By default, the background consists of an off-white ([cultured](https://encycolorpedia.com/f5f5f5)) rectangle over an ink-colored ([sumi](https://encycolorpedia.com/27221f)) canvas. The color of alerted text is set to a bright red called [corsa](https://encycolorpedia.com/d40000). These color definitions are included in `beamertheme*.sty`.

```tex
\definecolor{cultured}{HTML}{f5f5f5}
\definecolor{sumi}{HTML}{27221f}
\definecolor{corsa}{HTML}{d40000}
\definecolor{fern}{HTML}{4f7942}
\definecolor{cobalt}{HTML}{0047ab}
```

There are also two more colors, [fern](https://encycolorpedia.com/4f7942) and [cobalt](https://encycolorpedia.com/0047ab), which are currently unused in the design. If you wanted one of these to be the color of alerted text, then you would open `beamercolortheme*.sty` and look for:

```tex
\setbeamercolor*{alerted text}{fg=corsa}
```

Change `corsa` to some other color and you are set. Similar changes can be made to tweak the color of normal text, the background, or any other element of the layout. Of course, you can also define your own colors.

### Font weights

It is possible to change font styles and weights. Alegreya is a comprehensive family and comes with a variety of weights, as does its sister family Alegreya Sans. In addition to the usual bold set by `\bfseries`, Alegreya comes in medium, extra bold, and black. Alegreya Sans further comes in light and thin. These weights are set by commands like `\AlegreyaExtraBold` or `\AlegreyaSansThin` (see the [Alegreya README](https://mirrors.dotsrc.org/ctan/fonts/alegreya/README) for more details), and can be combined with `\scshape` or `\itshape` to produce a variety of effects.

The file `beamerfonttheme*.sty` sets the type for various elements of the layout. For example, the appearance of frame titles is determined by the following command:

```tex
\setbeamerfont{frame title}{size=\Large}
```

If you wanted to give frame titles a little bit more weight, you could write `{series=\AlegreyaMedium,size=\Large}`. If you wanted to make them slightly larger, you could change `\Large` to `\LARGE`.

By default, the theme uses serif type for most text and reserves sans-serif type for the presentation title, formatted in black weight, and URLs. It is possible to alter this behavior by modifying `beamerfonttheme*.sty`. For example, the appearance of the presentation title is determined by:

```tex
\setbeamerfont{title}{series=\AlegreyaSansBlack,size=\LARGE}
```

Changing `\AlegreyaSansBlack` to `\AlegreyaBlack` in this command makes the title serif like any other text. Deleting `\usefonttheme{serif}` near the top of the style file makes sans-serif type the new default for all text. Changing `\urlstyle{sf}` to `\urlstyle{same}` makes URLs appear like normal text, and deleting the line altogether resets them to true type.

### Figures

Figures are automatically set to old style, which is more varied and dynamic than the lining ("modern") style. If you wish to use lining figures instead, you can set these as default by opening `beamertheme*.sty` and removing the `osf` options from the packages `Alegreya` and `AlegreyaSans`.

Both old-style and lining figures are also available in a monospaced version, which is helpful for tables and other environments where numbers are displayed in column. It is possible to use monospaced versions locally with `\AlegreyaTOsF` (for old style) and `\AlegreyaTLF` (for lining). They can also be set as global defaults by loading packages with the `tf` option, as in:

```tex
\RequirePackage[osf,tf]{Alegreya}
\RequirePackage[osf,tf]{AlegreyaSans}
```

## Bugs

If you encounter any problem while using this package, please [create an issue](https://github.com/piazzai/arguelles/issues) on GitHub.
