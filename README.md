# paper-template

This repository contains the source files for our paper on PAPERTOPIC.

The `Paper` subdirectory contains the source for the actual paper (TeX, etc.).

The `Media` subdirectory should be used to store files that are not used in the final paper, but are used to generate content in the paper.  For instance, suppose you have a figure showing some geometry nicely rendered in Maya; the `Media` directory would contain the Maya source file, whereas the actual image might be stored in `Paper/images`.  Keeping the source files around is super useful for when you (inevitably) want to modify the figures 6 months later; keeping them separate from the paper source itself helps keeps things organized.  It also limits size bloat, in case you need to send the paper source to someone (e.g., journal editors will sometimes ask for the source).

## Starting a new project

The `Makefile` in the `Paper/` subdirectory is setup to allow you to easily build the paper and its bibliography.  You will likely want to rename a few files, so that they match your current project.  In particular:

`Paper/Paper.tex` -> `Paper/YourPaperName.tex`
`Paper/Paper.bib` -> `Paper/YourPaperName.bib`

You will then also need to change the `Makefile` so that the first line reads `TARGET = YourPaperName`, and the `.tex` file so that the bibliography line reads `\bibliography{YourPaperName}` (this line is near the end of the document, right before the graveyard).

## Building the paper

After changing the names (as above), you should just be able to type

   `make`

to build your paper.  On Mac, this will also open the paper PDF (on other platforms, you may get an error that the command `open` doesn't exist...).  Note that this command won't automatically build the bibliography; for that, you'll need to type

   `make bib`

(The reason for separating these commands is just that the bibliography takes a bit longer to build.)  Finally, you can build a diff of the current paper with an earlier version from the GitHub repo by typing

   `make diff`

This command will compile (and open) a PDF showing you what changed (by running a tool called `latexdiff`).  To set the previous version, you should use `git log` to find the commit number of the version of interest, and copy/paste this string into the `DIFFVERSION =` field of the `Makefile`.

## Compressing the paper

Even if you take care to compress your images, `pdflatex` often produces _extremely_ bloated PDF files (e.g., 80MB for a document that can nicely be compressed down to 10MB without any noticeable loss of fidelity).  A good way to get a high-quality compressed version of your final paper is to run the `File -> Save as Other -> Optimized PDF…` from Adobe Acrobat.  (Your readers will thank you!)

## Macros

The paper template includes a collection of standard macros, in the package `geometrycollective.sty`.  Take a look through these before you start writing—they're likely to save you some trouble, and make sure your document is nicely/consistently formatted.

You may also want to start a collection of macros specific to the current paper.  Some people like to just keep these at the top of the file; others like to create an external file, like `MyPaperMacros.tex`, which can be included via the command `\input{MyPaperMacros.tex}`.

## The graveyard 👻

Don't get spooked out—the "graveyard" is just a place to move text/figures that you don't want to use anymore, but you might want to refer to later.  Nothing included in this section will get compiled into the document (though you may still want to comment it out, to avoid confusion as you're skimming your source).

## Notes about diagrams

You'll save yourself time and trouble by creating figures that are compatible in shape, size, and style with the document style.  As of 2020, the main document font is Libertine 9pt.  The font for captions is Biolinium 8pt.  Both of these fonts are freely available online; just do a Google search and you'll find them.  The width of a single-column figure is 243.15pt; the width of a double-column figure is 510.30pt.  You can always get updated values directly via TeX; see the commands used in `Paper/template.tex`.

An Illustrator template that conforms to this specification is provided in `Media/ACM Two Column.ai`.  To install this template, just drop it in `/Applications/Adobe Illustrator/Support Files/New Document Profiles/en_US`, or the analogous path on your system.  You should now be able to select this template from the New Document dialog.

**A note about color and transparency.** As of 2020, `pdflatex` still has poor support for certain PDF features, especially transparent gradients.  Another common error is to save PDF files in CMYK color mode, which in some PDF viewers (like Preview on the Mac) can cause the whole page containing the image to look faded.  In general, you should double check that any included images render properly in your final document.  

## Linked vs. embedded images

In order to make figures editable by your coauthors, you should **ensure that all bitmap images are embedded in the PDF**.

In short, there are two ways an Adobe Illustrator document can refer to images:

- **Linked:** The file stores a path to an external bitmap file (JPG, PNG, etc.)
- **Embedded:** The bitmap image is stored exclusively in the Illustrator document, with no external links.

Where this gets confusing is that, if you save a file as PDF, Illustrator will _also_ embed a copy of the bitmap image in the PDF file.  However, if the Illustrator document used any external links, _the PDF will still not be editable by other users_.  Instead, loading the PDF into Illustrator will yield a message of the form

   ~~~
   Could not find the linked file "bitmap.jpg".  Choose Replace
   to select another file or Ignore to leave the link unchanged.
   ~~~

Unless your coauthors have a copy of `bitmap.jpg`, they will be unable to edit the file.

The solution is to make sure that all bitmap images are embedded.  There are two ways to make this happen:

1. (Safe way) Always import bitmap images by copying and pasting from another program (like Photoshop) into Illustrator.  This way you can be sure that Illustrator is not linking to an external file (because it does not know where the pixels on the clipboard came from!)
2. (Less safe way) Before saving your final document, select any bitmap images, then open up the `Links` palette from the `Window` menu.  In the upper-right corner of this palette there is a drop-down menu; select the `Embed Image(s)` option.

The reason that the "less safe" way is less safe is that you can easily forget to do it!

Note that in some cases it is convenient to link to external files, so that the Illustrator composition is automatically updated when the bitmap images change (e.g., when images are re-rendered).  In this case, a good practice is to keep a linked version in the `/Media` subdirectory, but embed all images before putting a final figure in the `/Paper/images` subdirectory.

