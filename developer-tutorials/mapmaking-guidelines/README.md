---
description: >-
  Making the maps look good and fun to play is a very important part in the
  success of Andor's Trail. Therefore, it is worth putting some effort into
  making them.
---

# Mapmaking Guidelines

See the [Map Editor](map-editor.md) to get some information about the layers used for Andor's Trail.

Also, see the Mapmaking tutorial for a guide with screenshots on how to make maps for Andor's Trail: [Map Making](map-making/)

We will still need several maps with:

* Any kind of outdoor maps with mountains, villages and towns, lakes, forests, roads, etc.
* Indoor maps for small houses, like the Fallhaven houses
* Dungeons

What map will you make, a deadly forest inhabited by bloodthirsty wolves or a damp dungeon filled with friendly necromancers? You decide.

## Quick version

If you quickly want to start making maps, do the following steps:

1. Download the Tiled map editor.
2. Download the latest [source code](https://github.com/AndorsTrailRelease/andors-trail) for Andor's Trail.
3. Examine an existing map.
4. Open the “template.tmx” map. Save that as a new file.
5. Post your map in the ([Andor's Trail forums](https://andorstrail.com)) or email the map to the project team (andor@andorstrail.com).

## Map Rules

All maps must follow these rules:

1. All maps in Andor's Trail must use the same tileset files (the minor split-up PNG files). We can, of course, add new things to the tileset if we find something that fits with the existing world.
2. All maps in Andor's Trail must have the same medieval look and feel.
3. Maps in Andor's Trail generally have a maximum of 30×30 tiles. While it might be technically feasible to import larger maps than that, there is currently no real benefit to making them larger than several smaller maps.
4. The tiles used from the tileset (.png files) need to make the map look as realistic as the existing maps. This means that there should be no straight edges, for example, when changing from grass to mountain. The tilesets allow smooth transitions for most ground types. The existing maps do not have any sharp edges because that makes them look unreal.
5. All maps must use the same standard for layer names. See the “template.tmx” file or the map edit wiki page for a list of available layers.
6. Each house floor, entrance, and mountain wall is generally two tiles high.
7. Since we generally display only 10×10 tiles of the map at a time in the game, we cannot have large areas of empty 10×10 tiles, as that would make the game look very uninteresting and odd.
8. The world should contain shadows on the right side of things that may cast a shadow. This is usually added to the “Above” layer so the player is partially shadowed, for example, when standing right next to an indoor wall.
9. Indoor maps should have walls on all sides except the southernmost border.&#x20;
10. Outdoor maps should indicate to the player which tiles lead to other maps. For example, a road that leads into the map edge.&#x20;
11. Map edges should fit with the map edges on the map they lead to. For example, if there are two trees north of the west map exit, there should be two trees north of the east map exit on the map that it leads to.&#x20;
12. Try not to make the maps look too “cute”. The world of Andor's Trail is a tough place. No excess in the amount of flowers. A stone or some dead grass fits better than a bunch of flowers.

There is a simple rule for placing the tops of the shadows:

* If the wall behind the shadow is straight, the shadow's top is straight as well.
* If the wall behind the shadow is an edge, the shadow's top is round.

![Shadow Tops](../../.gitbook/assets/shadow_tops.png)

## Alignment Rules

&#x20;Always align your maps to each other so they fit into the world map of Andor's Trail! Try to make the outdoor maps the **same size (30×30 tiles)** so they align more easily! The most common misalignments are trees, edges, and walls. The following pictures show the most common misalignments:

<div align="center"><img src="../../.gitbook/assets/alignmentmap_false.png" alt="Wrong Alignment"></div>



<div align="center"><img src="../../.gitbook/assets/alignmentmap_correct.png" alt=""></div>

To check whether your maps are aligned, follow these steps to create a worldmap:



1. Open Tiled (Click this [**link**](https://andorstrail.com/wiki/test/andors_trail_wiki/developer_section/map_making.html) if you haven't already installed the program.)
2. Load all the maps in Tiled that you want to place in a world map.
3. Import the template.tmx file and save it as a new file.
4. Enlarge the size of the former template.
5. Head over to the map you want to place on the world map.
6. Click the “Rectangular Select” button <img src="../../.gitbook/assets/selection_tool.png" alt="" data-size="original"> That can be found in the menu on the right of the “Eraser” button.
7. Select the “Ground” layer of your map.
8. Drag your mouse from the top-left corner to the bottom-right corner (Zoom out if required).
9. Copy the layer by using Control+C.
10. Paste the layer in the world map at an appropriate place (Press Control+V).
11. Keep repeating that procedure for every layer of your map until you have copied the whole map. (Only the layers “Ground”, “Objects”, and “Above” are essential).
12. Upon pasting your following map, leave one tile of space between the map you have pasted before. The tile of space isn’t counted as a real tile in the world map; it just shows the map change areas between the maps.
13. If you want to move the maps in your world map, head to Map/Offset Map.
14. You can create an image of the world map by clicking File/Save As Image. WARNING: Images rendered at a high zoom level will be huge!
15. Check for misalignments and correct them.
16. Now, your map is ready to present to the development team of Andor's Trail!
