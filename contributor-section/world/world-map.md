---
description: Map of the game world as of v0.7
---

# World Map

![This is how it looks like in version 0.7](../../.gitbook/assets/worldmap_v.0.7.png)

### Interesting things to know

When playing Andor's Trail, a screenshot is created upon entering every map. So it will even update areas that have been changed during a quest. The picture tokens are saved in andors-trail/worldmap as .png files. The worldmap.xml file stores the position of every map in the world map, and only the already explored locations are displayed. One tile of space is used to show the borders of the maps.

## How to create a world map

1. &#x20;Open Tiled (Click this [**link**](../../developer-tutorials/mapmaking-guidelines/map-editor.md) if you haven't already installed the program).
2. Load all the maps in Tiled that you want to place in a world map.
3. Import the template. Open the .tmx file and save it as a new file.
4. Enlarge the size of the former template.
5. Head over to the map you want to place on the world map.
6. &#x20;Click the “Rectangular Select” button that can be found in the menu to the right of the “Eraser” button.
7. Select the “Ground” layer of your map.
8. Drag your mouse from the top-left corner to the bottom-right corner (Zoom out if required).
9. Copy the layer by using Control+C.
10. Paste the layer in the world map at an appropriate place (Press Control+V).
11. Keep repeating that procedure for every layer of your map until you have copied the whole map. (Only the layers “Ground”, “Objects”, and “Above” are definitely needed).
12. Upon pasting your following map, leave one tile of space between the map you have pasted before. The tile of space isn’t counted as a real tile in the world map; it just shows the map change areas between the maps.
13. If you want to move the maps in your world map, head to Map/Offset Map.
14. You can create an image of the world map by clicking File/Save As Image. WARNING: Images rendered at high zoom levels will be huge!

### Download

The world map can also be rebuilt with Tiled. This program has been used to determine the correct coordinates for the position of the maps on the world map.

You can download the .tmx file from the [Github page](https://github.com/AndorsTrailRelease/andors-trail/blob/master/ProjectPage/maps/worldmap_v.0.7.tmx) (Click “view raw file” to download it)&#x20;

{% hint style="info" %}
Remember to put your downloaded file into the “xml” folder, where all maps are located. On the same level as “xml”, a “drawable” folder must be located, which includes all tilesets used for Andor's Trail.
{% endhint %}

