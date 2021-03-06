# Report

## How to use

You need to have the full [TeXLive](https://tug.org/texlive/) suit (or
[MacTeX](https://tug.org/mactex/)) to be able to create these LaTeX documents.
Some notes on requirements:

- The documents are compiled with LuaLaTeX, Biber and BibTeX.
- You'll use `latexmk` to continuously build the document(s).

## Configure `latexmk`

Create a new file in `$HOME` called `.latexmkrc`:

``` text
# Use LuaLaTeX
$lualatex='lualatex -interaction=nonstopmode -synctex=1 %O %S';
$preview_continuous_mode = 1;
# BibTeX with LuaLaTeX
$bibtex_use = 2;
# Create PDFs with LuaLaTeX
$pdf_mode = 4;
# TODO: Switch based on OS
$pdf_previewer = 'open -a skim';
# Remove SyncTeX generated stuff
@generated_exts = (@generated_exts, 'synctex.gz');
```

Please note the `TODO`, either comment out the line below or configure it to
open a PDF reader of your preference. On `macos` I recommend
[Skim](https://skim-app.sourceforge.io/), while on Linux I recommend
[zathura](https://pwmt.org/projects/zathura/). For this, simply change `'open -a
skim'` to `zathura`.

## Run `latexmk`

Now you should be ready, simply run `latexmk <filename>` in your terminal and
everything will start compiling for you and will open the created PDF file.

## Editing

You do you, there are a thousand different editors for LaTeX. There are however
some tips I can come with:

1. The style I personally prefer for references in `BibTeX` are
   `<authorLastName><year><FirstWordFromTitle>`. Personal preference obviously.
   The reference style used in this report is the IEEE style, which is the most
   prevalent one within computer science.
2. Labels are really useful, use them within sections, for figures, images and
   so on.
3. Don't commit the generated PDF until you are finished with it, Git doesn't
   work very well with blobs so it ends up tracking each commited version of the
   file, causing the size of the repository to become stupid large.
