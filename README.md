# paper-template

This repository contains the source files for our paper on PAPERTOPIC.

The `Paper` subdirectory contains the source for the actual paper (TeX, etc.).

The `Media` subdirectory should be used to store files that are not used in the final paper, but are used to generate content in the paper.  For instance, suppose you have a figure showing some geometry nicely rendered in Maya; the `Media` directory would contain the Maya source file, whereas the actual image might be stored in `Paper/images`.  Keeping the source files around is super useful for when you (inevitably) want to modify the figures 6 months later; keeping them separate from the paper source itself helps keeps things organized.  It also limits size bloat, in case you need to send the paper source to someone (e.g., journal editors will sometimes ask for the source).

# Formatting diagrams

You'll save yourself time and trouble by creating figures that are compatible in shape, size, and style with the document style.  As of 2020, the main document font is Libertine 9pt.  The font for captions is Biolinium 8pt.  Both of these fonts are freely available online; just do a Google search and you'll find them.  The width of a single-column figure is 243.15pt; the width of a double-column figure is 510.30pt.  You can always get updated values directly via TeX; see the commands used in `Paper/template.tex`.

An Illustrator template that conforms to this specification is provided in `Media/ACM Two Column.ai`.  To install this template, just drop it in `/Applications/Adobe Illustrator/Support Files/New Document Profiles/en_US`, or the analogous path on your system.  You should now be able to select this template from the New Document dialog.

