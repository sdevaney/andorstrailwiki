---
description: This is a tutorial on how to make beautiful looking maps for Andor's Trail.
---

# Map Making

## Preparing the environment

Before we begin, let's set up our environment with the program and files that we will need.

1. Download [Tiled](https://mapeditor.org) and install it.
2. Download the Andor's Trail source code by either downloading the prepackaged [source files](https://github.com/Zukero/andors-trail/) or by downloading the source code via GitHub (Click “Download zip” in the bottom right-hand corner).
3.  Unpack the source files. It doesn't matter where you place the files on your drive; just remember the directory you placed them in. You should get a directory structure something like the following: &#x20;

    <img src="../../../.gitbook/assets/directory structure.png" alt="" data-size="original">
4.  Inside the directory AndorsTrail/res/xml should be a bunch of files ending in tmx. These are the existing maps. We will be using them. Open Tiled and open the file “home.tmx” to make sure it shows up correctly. You should see the starting map in the map editor. Examine it if you like. In particular, note the layers on the right. Try switching some layers off to see what happens in the editor. &#x20;

    <img src="../../../.gitbook/assets/home3.png" alt="" data-size="original">
5. If the file cannot be opened, make sure you are using the same directory structure as listed above. The map files use other files in the “drawable” directory, so make sure this directory is accessible. Ok, your environment is now ready for making maps.
6. Ok, your environment is now ready for making maps.

### Other Helpful Pages

&#x20;For more information about layers, please browse the [Map Editor](../map-editor.md).

## Making a New Map

&#x20;Start by opening the file “template.tmx” in Tiled. This file contains the necessary setup for the tiles we use and the layer names used by Andor's Trail. It should be an empty 30×30 map.&#x20;

![You might want to press ctrl-g to toggle the visibility of the grid.](../../../.gitbook/assets/template3.png)

Use “save as” to save the file to something else. I'm going to make a dungeon map, so I'll save my file as “scarydungeon1.tmx”.

![](../../../.gitbook/assets/mapmaking3.jpeg)

Let's start by making the map the size that we want. Go to “Map” (in menu) → “Resize map” and enter the size you want. I'm going to make my map a 15×11 map.

![](../../../.gitbook/assets/scarydungeon1.png)

Paint the ground in the tile type you want by using the paint tool. For my dungeon, I like to use the following tile type located in map\_ground\_1.

![Hint: Right-clicking a tile copies it. That is much faster than selecting an already used tile in the tilesets window.](../../../.gitbook/assets/scarydungeon6.png)

I usually start by drawing the walls to create the outline of the map by selecting the stamp brush tool. Walls are usually two tiles high before hitting the ceiling. Notice how I can select two tiles at the same time and draw them. Note also that since these cover the whole tile, I can place them in the “Ground” layer (which slightly increases the performance when drawing the map).

![](../../../.gitbook/assets/scarydungeon7.png)

There are a couple of things to notice:

* Leave a space for the entrance.
* Try not to make too many straight lines. In my map, I try to outline “round” as much as possible without any straight edges.

After that, I'm drawing the wall corners. They are used to make the edges smoother.

![](../../../.gitbook/assets/scarydungeon8.png)

Let's finish the walls. For dungeon walls, four different tile types have their edges in four different directions. I'm going to use these as the tops of the walls.

![](../../../.gitbook/assets/scarydungeon9.png)

Finally, we fill the rest with the non-edge wall type.

![](../../../.gitbook/assets/scarydungeon10.png)

I want my dungeon walls to use a partially transparent tile, so I need to place them in “Objects”. To finish the walls we need to place the bottom and top corners.

![](../../../.gitbook/assets/scarydungeon11.png)

![](../../../.gitbook/assets/scarydungeon12.png)

Ok, this is really starting to look like a map now. Let's add some scary looking graves and other things.

![](../../../.gitbook/assets/scarydungeon13.png)

![](../../../.gitbook/assets/scarydungeon14.png)

![](../../../.gitbook/assets/scarydungeon15.png)

![](../../../.gitbook/assets/scarydungeon16.png)

I also want an exit to the north. Let's add a cave opening.

![](../../../.gitbook/assets/scarydungeon17.png)

What could be scarier than some broken barrels and crates with cobwebs, right? Let's add that.

![](../../../.gitbook/assets/scarydungeon18.png)

![](../../../.gitbook/assets/scarydungeon19.png)

The main parts of this map are now complete. Let's add some more clutter to make the map look even more beautiful.

![](../../../.gitbook/assets/scarydungeon20.png)

To make the crates look even creepier, I'm adding some black dust to the “Above” layer. Otherwise, the crate underneath it would be replaced by the dust.

![](../../../.gitbook/assets/scarydungeon21.png)

![](../../../.gitbook/assets/scarydungeon22.png)

![](../../../.gitbook/assets/scarydungeon23.png)

Let's add shadows to the “Above” layer to give the false impression that the map is somehow lit. There is a simple rule for placing the top of the shadow:

* If the wall behind the shadow is straight, the shadow's top is straight as well.
* If the wall behind the shadow is an edge, the shadow's top is round.

![](../../../.gitbook/assets/shadow_tops.png)

I applied that rule to the shadows in our cave:

![](../../../.gitbook/assets/scarydungeon32.png)

Do you see the shadow tile under the stone corner? I did that by placing the shadow in “Objects” and placing the stone corner in “Above”. Due to this change, the shadow looks more “connected” to the walls.

![](../../../.gitbook/assets/scarydungeon33.png)

The visible parts of the map are now done. Let's add the walkable layer. Every tile that is covered by “Walkable” is inaccessible. The bottom tile of the entrance to the north should be reachable, though.

![](../../../.gitbook/assets/scarydungeon34.png)

Let's add some monsters to the map. Monsters can be found in the monster resource files. If you have downloaded the source code, you can find the monster list file in res/raw/monsterlist\_placeholder.json. Otherwise, you can browse it online from [Github.](https://github.com/Zukero/andors-trail/)

To make a new monster, you would have to add it to the monster resource file, and that is a tutorial on its own. Let's reuse some old monsters to make it easy. I want to have a basilisk on my map (from the snake cave outside Crossglen), and the basilisk has monster spawn group “cavesnake2\_boss”.

Let's create a spawn area by changing to the “Spawn” layer and selecting the “Insert Rectangle” tool in the menu. Now, I'm placing an area on the map (draw from top left to bottom right).

* Enable “Snap to grid” under “View”. Due to that feature, the grid has the same size as the tiles.
* Please leave one tile of space between entrances and the spawn areas.

![](../../../.gitbook/assets/scarydungeon35.png)

Right-click it and select properties, and let's make this a “spawn” type, and specify the monster that we want to spawn here. I can also specify that I want two of them by supplying a “quantity” property.

![](../../../.gitbook/assets/scarydungeon28.png)

Ok, let's add some logic to what happens when we enter that north cave. Switch to the “Mapevents” layer and draw a new area on the tile that is the cave exit.

![](../../../.gitbook/assets/scarydungeon36.png)

Right click it and select properties, and make the type to “mapchange”. With the “map” and “place” properties, we can specify where the player will end up when stepping on this tile. The “map” should be some other map name, and “place” a name of a mapchange area on that map. (The cardinal points are most commonly used as “place” property.)

![](../../../.gitbook/assets/scarydungeon30.png)

I'm making the player end up on the “south” entrance on the next cave in “scarydungeon2”. I should make sure to place a mapchange area with that name on that map when I make it. The “south” area on “scarydungeon2” should also point to the “north” mapchange area on “scarydungeon1”.

That's it. Map complete.

![](../../../.gitbook/assets/scarydungeon37.png)

## Publishing the Map

To make the map end up as an official map in Andor's Trail, you will need to do the following:

Make sure the map follows the [Mapmaking Guidelines](../).

Post your map in the [Andor's Trail forums](https://andorstrail.com) or create a [GitHub pull request ](https://github.com/Zukero/andors-trail)with it.

Thank you for reading the tutorial. We look forward to seeing your beautiful maps!
