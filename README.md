<!--
arguelles v2.5.0
author: Michele Piazzai
https://piazzai.github.io
license: MIT
-->

# arguelles

Argüelles is a beamer theme that helps you create beautiful presentations. It aims for simplicity and readability by following best practices of graphic design. The layout is elegant but subtle, so as to keep the audience's attention on your content. This is brought to life by Alegreya, one of the 53 Fonts of the Decade selected by the Association Typographique Internationale (2011).

The theme requires the following packages to be installed on your computer: [inputenc](https://ctan.org/pkg/inputenc) (if compiling with pdfLaTeX), [fontenc](https://ctan.org/pkg/fontenc), [alegreya](https://ctan.org/pkg/alegreya) and [eulervm](https://ctan.org/pkg/eulervm) (unless you are opting out of Alegreya fonts), [mathalpha](https://www.ctan.org/pkg/mathalpha), [microtype](https://ctan.org/pkg/microtype), [fontawesome5](https://ctan.org/pkg/fontawesome5), [opencolor](https://www.ctan.org/pkg/opencolor), [enumitem](https://www.ctan.org/pkg/enumitem), [parskip](https://www.ctan.org/pkg/parskip), [pgf](https://ctan.org/pkg/pgf), and [tcolorbox](https://ctan.org/pkg/tcolorbox). These are included in common LaTeX distributions, such as MiKTeX and TeXLive, and availab.

## Demo

The files `demo-arguelles.tex` and `demo-arguelles.pdf` demonstrate the main features of the theme.

![](https://github.com/piazzai/arguelles/blob/master/demo/demo-arguelles.gif)

## Installation

Argüelles is hosted on CTAN and distributed as part of MikTex and TeXLive. It can also be installed manually by cloning this repository in your `$HOME/texmf/tex/latex` folder, which is automatically searched by LaTeX. If you do not have this folder, you can create one ([read how](https://www.ias.edu/math/computing/faq/local-latex-style-files)).

## Usage

By default, the theme uses Alegreya (serif) for body text and math type, and Alegreya Sans for the presentation's title and subtitle. Some math symbols are taken from the Euler font, as they look better than default symbols when paired with Alegreya.

Loading the theme with the `sans` option makes Alegreya Sans default also for body text, keeping serif only for math type. Because sans serif is more space-efficient, this option can be useful for slides that contain a lot of text and bullet points. The `noalegre` option removes the Alegreya and Euler dependencies entirely: the theme compiles with LaTeX's default fonts and you can override them with any typeface of your choice.

The `frameno` option adds frame numbering in the bottom right corner of each frame. Frame numbers remain hidden on title and plain frames. They can also be enabled globally but suppressed on individual frames by adding the `noframenumbering` option to the `frame` environment, as in:

```tex
\begin{frame}[noframenumbering]
...
\end{frame}

```

The `splitnav` option makes the navigation bar in the headline display only the current section and its frames, as opposed to all section and all frames. This could be preferable if your presentation has only a few sections, which do not adequately fill the headline, or if it has a lot of sections and the headline looks too crowded.

## Customization

It is possible to change parts of the theme by altering the style files. There are five such files:

-   `beamercolorthemeArguelles.sty` sets the colors;
-   `beamerfontthemeArguelles.sty` sets font styles and weights;
-   `beamerinnerthemeArguelles.sty` sets the appearance of frames;
-   `beamerouterthemeArguelles.sty` sets the appearance of headline and frame titles;
-   `beamerthemeArguelles.sty` loads required packages, and defines custom colors and commands.

### Colors

The theme ships with the [opencolor](https://www.ctan.org/pkg/opencolor) package, which provides color definitions for the [Open Color](https://yeun.github.io/open-color/) library. By default, the background and foreground are set to `oc-gray-0` and `oc-gray-9`. Body text is set to `oc-gray-8`. The color of alerted text is `oc-red-9`. Shaded text in the table of contents is `oc-gray-6`.

These settings are provided in `beamercolorthemeArguelles.sty` and can be customized using any default or opencolor name. For example:

```tex
\setbeamercolor*{structure}{bg=oc-blue-0,fg=black!80}
```

See the [opencolor docs](https://github.com/piazzai/opencolor/blob/master/README.md) for additional details.

### Font weights

Alegreya is a comprehensive family and comes with a variety of weights, as does its sister family Alegreya Sans. In addition to the usual bold provided by `\bfseries`, Alegreya comes in medium, extra bold, and black. Alegreya Sans further comes in light and thin. These weights are set by commands like `\AlegreyaExtraBold` or `\AlegreyaSansThin`, as explained in the [Alegreya docs](https://mirrors.ctan.org/fonts/alegreya/README), and can be combined with `\scshape` or `\itshape` to produce a variety of effects.

The file `beamerfontthemeArguelles.sty` sets the type for various elements of the layout. For example, the appearance of frame titles is given by:

```tex
\setbeamerfont{frame title}{size=\Large}
```

If you want to give frame titles a little bit more weight, you can add `,series=\AlegreyaMedium` to the second argument. If you want to make them slightly larger, you can write `size=\LARGE`.

By default, the theme uses serif type for body text and reserves sans-serif type for the presentation title, formatted in black weight. It is possible to modify this behavior by rewriting parts of `beamerfontthemeArguelles.sty`. For example, the appearance of the presentation title, assuming you are not opting out of Alegreya fonts, is set by:

```tex
\setbeamerfont{title}{series=\AlegreyaSansBlack,size=\LARGE}
```

Changing `\AlegreyaSansBlack` to `\AlegreyaBlack` in this line sets the title to serif, keeping the same weight. You can modify other parts of this file for greater customization. For example, changing `\urlstyle{same}` to `\urlstyle{sf}` makes URLs sans-serif, and deleting the line altogether resets them to true type.

### Figures

Figures are automatically set to old style, which is more varied and dynamic than the lining style. If you wish to use lining figures instead, you can set these as default by opening `beamerthemeArguelles.sty` and removing the `osf` options from the packages `Alegreya` and `AlegreyaSans`.

Both old-style and lining figures are also available in a monospaced version, which is helpful for tables and other settings where numbers are displayed in column. It is possible to use monospaced versions locally with the commands `\AlegreyaTOsF` (for old style) and `\AlegreyaTLF` (for lining), as explained in the [Alegreya docs](https://mirrors.ctan.org/fonts/alegreya/README). They can also be set as global defaults by loading packages with the `tf` option:

```tex
\RequirePackage[osf,tf]{Alegreya}
\RequirePackage[osf,tf]{AlegreyaSans}
```

## Known issues

#### When using subsections, frame bullets appear on multiple lines

Argüelles is built with the intention to reserve as much space as possible for the content of your slides. When using subsections, the progress bar in the headline places frame bullets on multiple lines, which takes space away from your content. The theme does not handle this well. You can force the bullets to appear on the same line by loading beamer with the `compress` option, as below:

```tex
\documentclass[compress]{beamer}
```

#### When using notes on second screen, frame text becomes white

This is a [known problem](https://github.com/josephwright/beamer/issues/337) caused by beamer's `show notes on second screen` option when the document is compiled using XeLaTeX. It is not an issue caused by the theme. It can be fixed by switching to pdfLaTeX or by adding the following code to your document's preamble:

```tex
\makeatletter
\def\beamer@framenotesbegin{% at beginning of slide
    \usebeamercolor[fg]{normal text}%
    \gdef\beamer@noteitems{}%
    \gdef\beamer@notes{}%
}
\makeatother
```

If you find any other problem using this package, please [open an issue](https://github.com/piazzai/arguelles/issues).
