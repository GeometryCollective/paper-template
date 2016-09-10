# paper-template

This repository contains a starting template for new paper submissions.  These templates build off standard templates (e.g., SIGGRAPH, TOG, SGP, etc.), but with common modifications (e.g., better typography, useful macros, etc.).

**Typical usage:** When you want to start a new paper, you should:

* fork this repository
* decide which template you want to use
* start hacking on your paper in that template directory
* _optional:_ kill the other templates (though they may prove useful if you later decide to change venues, e.g., TOG to SIGGRAPH)

The `Media` subdirectory should be used to store files that are not used in the final paper, but are used to generate content in the paper.  For instance, suppose you have a figure showing some geometry nicely rendered in Maya; the `Media` directory would contain the Maya source file, whereas the actual image might be stored in `SIGGRAPH/images`.  Keeping the source files around is super useful for when you (inevitably) want to modify the figures 6 months later; keeping them separate from the paper source itself helps keeps things organized.  It also limits size bloat, in case you need to send the paper source to someone (e.g., journal editors will sometimes ask for the source).