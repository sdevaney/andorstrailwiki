# Contributing Code

Andor's Trail is developed as open source, meaning anyone can help add content to the game. If you are experienced in development, you are welcome to help add code to the game.

The source code for Andor's Trail is available in Git from this [page](https://github.com/Zukero/andors-trail/).

The git repository root contains the following subdirectories:

AndorsTrail - This is the main source code for the game itself.

## Quick introduction

If you want to get acquainted with the code, you are encouraged to download it and play with it yourself. The best code additions usually come from players who want to fix an issue that would enhance their gameplay, so if you find something you want to add or fix, please try adding it to the code.

If you want other inspirations for things that need to be done in the code, see the issue tracker list, or try one of the following:

* How are the player stats determined?
* How is damage determined when an attack is made?
* What code handles map transitions when the player leaves a map?
* What happens when the player rests?

## Guidelines

Code that is added to Andor's Trail should follow these guidelines:

1. [DRY](http://en.wikipedia.org/wiki/Don't_repeat_yourself)
2. Begin with code that works, then refactor it. Not the other way around. [YAGNI](http://en.wikipedia.org/wiki/You_ain't_gonna_need_it)
3. &#x20;We try to follow [existing conventions](https://petroware.no/javastyle.html) regarding naming and casing.
4. Try not to use abstract or virtual methods unless necessary.
5. If the code is frequently run, such as in a response to a user action, avoid creating too many new object instances (“new”:ing objects). Not all devices have a good GC.
6. No static fields unless they are constants.

## Debug resources

When developing the game code, there are a couple of debug parameters that you can set to make the development process more manageable. In the file AndorsTrailApplication, you can enable the following parameters:

**DEVELOPMENT\_DEBUGRESOURCES** - Only loads some resources during startup, not all monsters, items, or maps. The player will be placed on a debug map instead of the “real” world. Enabling this dramatically speeds up game startup time.\
**DEVELOPMENT\_QUICKSTART** - When the game starts, it automatically continues from the last game. This way you don't have to see the startup screen when developing.\
**DEVELOPMENT\_DEBUGBUTTONS** - Enabled cheat buttons to spawn new monsters, add exp or gold, and change the player combat parameters.\
**DEVELOPMENT\_VALIDATEDATA** - Enables many consistency checks on data loaded from resources. For example, checks that all items exist and that the dialog has correct references.\
**DEVELOPMENT\_DEBUGMESSAGES** - Enables logging to the catalog. With this disabled, no output will be written to the system log.

For a release version, all of these parameters are, of course, set to false.

