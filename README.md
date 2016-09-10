# paper-template

This repository contains the source files for our paper on PAPERTOPIC.

The `Paper` subdirectory contains the source for the actual paper (TeX, etc.).

The `Media` subdirectory should be used to store files that are not used in the final paper, but are used to generate content in the paper.  For instance, suppose you have a figure showing some geometry nicely rendered in Maya; the `Media` directory would contain the Maya source file, whereas the actual image might be stored in `Paper/images`.  Keeping the source files around is super useful for when you (inevitably) want to modify the figures 6 months later; keeping them separate from the paper source itself helps keeps things organized.  It also limits size bloat, in case you need to send the paper source to someone (e.g., journal editors will sometimes ask for the source).
