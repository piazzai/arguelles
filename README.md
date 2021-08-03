# arguelles

Argüelles is a beamer theme that helps you create beautiful presentations. It aims for simplicity and readability by following best practices of graphic design. The layout is elegant but subtle so as to keep the audience's attention on your content. This is brought to life by Alegreya, one of the 53 Fonts of the Decade selected by the Association Typographique Internationale (2011).

The theme requires the packages [tikz](https://ctan.org/pkg/pgf), [microtype](https://ctan.org/pkg/microtype), [Alegreya/AlegreyaSans](https://ctan.org/pkg/alegreya), [euler](https://ctan.org/pkg/euler), and [fontawesome](https://ctan.org/pkg/fontawesome) to be installed on your computer. These are included in most LaTeX distributions, such as [MiKTeX](https://ctan.org/pkg/miktex) and [TeXLive](https://ctan.org/pkg/texlive).

### Table of contents

-   [Demo](#demo)
-   [Installation](#installation)
-   [Customization](#customization)
    -   [Colors](#colors)
    -   [Font weights](#font-weights)
    -   [Figures](#figures)

* * *

## Demo

The files `demo.tex` and `demo.pdf` demonstrate the main features of the theme.

![](https://github.com/piazzai/arguelles/blob/master/demo/titlepage.jpg)
![](https://github.com/piazzai/arguelles/blob/master/demo/subtitle.jpg)
![](https://github.com/piazzai/arguelles/blob/master/demo/title.jpg)
![](https://github.com/piazzai/arguelles/blob/master/demo/plain.jpg)
![](https://github.com/piazzai/arguelles/blob/master/demo/standout.jpg)
![](https://github.com/piazzai/arguelles/blob/master/demo/closing.jpg)

## Installation

The theme is not yet hosted on CTAN. To install it, clone the repository and place all `*.sty` files in the directory of your beamer presentation. Then, just write `\usetheme{Arguelles}` in the document preamble.

If you plan to use the theme for multiple presentations, or simply do not want to clutter your directory, you can move the `*.sty` files to `$HOME/texmf/tex/latex`, which is automatically searched by LaTeX. If you do not have such folder yet, you can create one ([read here](https://www.ias.edu/math/computing/faq/local-latex-style-files)).

## Customization

It is possible to change parts of the theme by altering the `*.sty` files. There are five such files:

-   `beamercolortheme*.sty` sets the colors;
-   `beamerfonttheme*.sty` sets font styles and weights;
-   `beamerinnertheme*.sty` sets the appearance of frames;
-   `beameroutertheme*.sty` sets the appearance of headline and frame titles;
-   `beamertheme*.sty` loads required packages and defines custom colors and commands.

### Colors

Suppose you want to change the color scheme. By default, the theme's background consists of an off-white rectangle, with hex F5F5F5 ([cultured](https://encycolorpedia.com/f5f5f5)), over an ink-colored canvas with hex 27221F ([sumi](https://encycolorpedia.com/27221f)). The color of alerted text is set to a bright red called [corsa](https://encycolorpedia.com/d40000), with hex D40000. These color definitions are included in `beamertheme*.sty`.

```tex
\definecolor{cultured}{HTML}{f5f5f5}
\definecolor{sumi}{HTML}{27221f}
\definecolor{corsa}{HTML}{d40000}
\definecolor{fern}{HTML}{4f7942}
\definecolor{cobalt}{HTML}{0047ab}
```

There are also two more colors, called [fern](https://encycolorpedia.com/4f7942) and [cobalt](https://encycolorpedia.com/0047ab), which are currently unused in the design. If, for example, you wanted one of these to be the color of alerted text, then you would open `beamercolortheme*.sty` and look for:

```tex
\setbeamercolor*{alerted text}{fg=corsa}
```

Change the color name after `fg=` and you are set. Similar changes can be made to tweak the color of normal text, background, or any other element of layout. Naturally, you can also define your own colors.

### Font weights

Just like colors, it is possible to change font styles and weights. Alegreya is a comprehensive family and comes with a variety of weights, as does its sister family Alegreya Sans. In addition to the usual bold called by `\bfseries`, Alegreya also comes in medium, extra bold, and black. Alegreya Sans further comes in light and thin. These weights are called by commands like `\AlegreyaExtraBold` or `\AlegreyaSansThin` (see the [Alegreya package README](https://www.ctan.org/pkg/alegreya) for full details), and can be combined with `\scshape` or `\itshape` to produce a variety of effects.

The file `beamerfonttheme*.sty` sets the type for various elements of the layout. For example, the appearance of frame titles is governed by the following line of code:

```tex
\setbeamerfont{frame title}{size=\Large}
```

If you wanted to give frame titles a little bit more weight, you could set `{series=\AlegreyaMedium,size=\Large}`. If you wanted to make them slightly larger, you could set `{size=\LARGE}`.

By default, the theme uses serif Alegreya and reserves sans-serif type for the presentation title, formatted in Alegreya Sans Black, and URLs. It is possible to alter this behavior by modifying `beamerfonttheme*.sty`. For example, the appearance of the presentation title is given by:

```tex
\setbeamerfont{title}{series=\AlegreyaSansBlack,size=\LARGE}
```

Setting this to `{series=\AlegreyaBlack,size=\LARGE}` makes the title serif while keeping the same weight. Deleting `\usefonttheme{serif}` near the beginning of the file resets sans-serif type as default for all text, unless otherwise specified. Changing `\urlstyle{sf}` to `\urlstyle{same}` makes URLs appear just like normal text, and deleting the line altogether resets them to true type.

### Figures

Figures are automatically set to old style, which is more varied and dynamic than the lining ("modern") style. If you wish to use lining figures instead, you can set these as default by opening `beamertheme*.sty` and removing the `osf` options from the packages `Alegreya` and `AlegreyaSans`.

Both old-style and lining figures are also available in a monospaced version, which is helpful for tables and other environments where numbers are displayed in column. It is possible to use these versions locally with the commands `\AlegreyaTOsF` (for old style) and `\AlegreyaTLF` (for lining). They can also be set as global defaults by loading packages with the `tf` option, as in:

```tex
\RequirePackage[osf,tf]{Alegreya}
\RequirePackage[osf,tf]{AlegreyaSans}
```
