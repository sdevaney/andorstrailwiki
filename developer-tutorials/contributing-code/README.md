# Contributing Code

Andor's Trail is developed as [open-source](http://en.wikipedia.org/wiki/Open-source_software), roughly meaning that anyone can help add content to the game. If you are experienced with development, you are welcome to help in adding code to the game.

The source code for Andor's Trail is available in Git from this [page](https://github.com/Zukero/andors-trail/).

The git repository root contains the following subdirectories:

AndorsTrail - This is the main source code for the game itself.

## Quick introduction

If you want to get acquainted with the code, you are encouraged to download the code and start playing with it yourself. The best code additions are usually from players that want to fix some issue that would enhance their gameplay, so if you find something that you want to add or fix, then please try adding that to the code.

If you want other inspirations to things that need to be done in the code, see the issue tracker list, or try one of the following:

* How is the player stats determined?
* How is damage determined when an attack is made?
* What code handles map transitions when the player leaves a map?
* What happens when the player rests?

## Guidelines

Code that is added to Andor's Trail should follow these guidelines:

1. [DRY](http://en.wikipedia.org/wiki/Don%27t_repeat_yourself)
2. Begin with code that works, then refactor it. Not the other way around. [YAGNI](http://en.wikipedia.org/wiki/You_ain%27t_gonna_need_it)
3.  We try to following [existing conventions](https://petroware.no/javastyle.html) regarding naming and casing.
4. Try not to use abstract or virtual methods unless absolutely necessary.
5. If the code is frequently run, such as a response to a user action, try not to create too many new object instances \(“new”:ing objects\). Not all devices have a good GC.
6. No static fields unless they are constants.

## Debug resources

When developing the game code, there are a couple of debug parameters that you can set to make the development process easier. In file AndorsTrailApplication?.java, you can enable the following parameters:

**DEVELOPMENT\_DEBUGRESOURCES** - Only loads some resources duing startup, not all monsters, items or maps. The player will be placed on a debug map instead of the “real” world. Enabling this speeds up the game startup time dramatically.  
**DEVELOPMENT\_QUICKSTART** - When the game starts, automatically continues the last game. This ay you don't have to see the startup screen when developing.  
**DEVELOPMENT\_DEBUGBUTTONS** - Enabled cheat buttons to spawn new monsters, add exp or gold and change the player combat parameters.  
**DEVELOPMENT\_VALIDATEDATA** - Enables a lot of consistency checks on the data being loaded from resources. For example, checks that all items exists and that the dialog has correct references.  
**DEVELOPMENT\_DEBUGMESSAGES** - Enables logging to catlog. Witht his disabled, no output will be placed in the system log whatsoever.

For a release version, all of these parameters are ofcourse set to false.



