# arguelles

Argüelles is a beamer theme that helps you create beautiful presentations. It aims for simplicity and readability by following best practices of graphic design. The layout is elegant but subtle so as to keep the audience's attention on your content. This is brought to life by Alegreya, one of the 53 Fonts of the Decade selected by the Association Typographique Internationale (2011).

The theme requires the packages [tikz](https://ctan.org/pkg/pgf), [microtype](https://ctan.org/pkg/microtype), [Alegreya/AlegreyaSans](https://ctan.org/pkg/alegreya), [euler](https://ctan.org/pkg/euler), and [fontawesome](https://ctan.org/pkg/fontawesome) to be installed on your computer. These are included in most LaTeX distributions, such as [MiKTeX](https://ctan.org/pkg/miktex) and [TeXLive](https://ctan.org/pkg/texlive).

### Table of contents

-   [Demo](#demo)
-   [Installation](#installation)
-   [Customization](#customization)

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

It is possible to change parts of the theme by altering the `*.sty` files. There are five files:

-   `beamercolortheme*.sty` sets the color scheme;
-   `beamerfonttheme*.sty` sets font styles and weights;
-   `beamerinnertheme*.sty` sets the appearance of frames;
-   `beameroutertheme*.sty` sets the appearance of headline and frame titles;
-   `beamertheme*.sty` loads packages and defines custom colors and commands.

Suppose you want to change the color scheme. By default, the theme's background consists of an off-white rectangle, with hex F5F5F5 ([cultured](https://encycolorpedia.com/f5f5f5)), over an ink-colored canvas with hex 27221F ([sumi](https://encycolorpedia.com/27221f)). The color of alerted text is set to a bright red called [corsa](https://encycolorpedia.com/d40000), with hex D40000. These color definitions are included in `beamertheme*.sty`.

```tex
\definecolor{cultured}{HTML}{f5f5f5}
\definecolor{sumi}{HTML}{27221f}
\definecolor{corsa}{HTML}{d40000}
\definecolor{cobalt}{HTML}{0047ab}
```

There is also a fourth color, a shade of blue called [cobalt](https://encycolorpedia.com/0047ab), which is currently unused in the design. If, for example, you wanted this to be the color of alerted text, then you would open `beamercolortheme*.sty` and change `\setbeamercolor*{alerted text}{fg=corsa}` to `\setbeamercolor*{alerted text}{fg=cobalt}`. Similar tweaks can be made for the color of normal text, the background, or any other element of the layout. Naturally, you can also define your own colors: [here](https://coolors.co/generate) is a handy online tool to quickly generate good-looking color schemes.

Just like colors, it is possible to change font styles and weights. Alegreya is a comprehensive font family and comes with a variety of weights, as does its sister family Alegreya Sans. In addition to the usual `\bfseries`, `\itshape`, and `\scshape`, Alegreya also comes in medium, extra bold, and black. Alegreya Sans further comes in light and thin. These styles are called by commands like `\AlegreyaExtraBold` or `\AlegreyaSansThin` (see the [Alegreya package README](https://www.ctan.org/pkg/alegreya)), and can be combined with `\scshape` or `\itshape` so as to produce a variety of effects.

The file `beamerfonttheme*.sty` sets the type for various elements of the layout. For example, the appearance of frame titles is governed by `\setbeamerfont{frame title}{size=\Large}`. If you wanted to give frame titles a little bit more weight, you could set `\setbeamerfont{frame title}{series=\AlegreyaMedium,size=\Large}`. If you wanted to make them slightly larger, you could set `\setbeamerfont{frame title}{size=\LARGE}`.

By default, the theme uses serif Alegreya and reserves sans-serif type for the presentation title, formatted in Alegreya Sans Black, as well as URLs. It is possible to alter this behavior by modifying `beamerfonttheme*.sty`. For example, changing `\setbeamerfont{title}{series=\AlegreyaSansBlack,size=\LARGE}` to `\setbeamerfont{title}{series=\AlegreyaBlack,size=\LARGE}` sets the presentation title to serif while keeping the black weight. Deleting `\usefonttheme{serif}` resets sans-serif type as the default for all text, unless otherwise specified. Changing `\urlstyle{sf}` to `\urlstyle{same}` makes URLs appear just like normal text, and deleting the line altogether resets them to true type.

Figures are automatically set to old style, which is more varied and dynamic. If you wish to use lining figures instead, you can set these as default by opening `beamertheme*.sty` and removing the `osf` options from the packages `Alegreya` and `AlegreyaSans`. Both old-style and lining figures are also available in a monospaced version, which is helpful for tables and other environments where numbers are displayed in column. It is possible to use these versions locally with the commands `\AlegreyaTOsF` (for old style) and `\AlegreyaTLF` (for lining).
