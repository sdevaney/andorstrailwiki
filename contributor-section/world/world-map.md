---
description: Map of the game world as of v0.7
---

# World Map

![This is how it looks like in version 0.7](../../.gitbook/assets/worldmap_v.0.7.png)

### Interesting things to know

When playing Andor's Trail, a screenshot is created upon entering every map. So it will even update areas having been changed during a quest. The pictures token are saved in andors-trail/worldmap as .png files. There is a worldmap.xml file in which the position of every map in the world map is stored and only the already explored locations will be displayed. One tile of space is used to show the borders of the maps.

## How to create a world map

1.  Open Tiled \(Click this [**link**](../../developer-tutorials/mapmaking-guidelines/map-editor.md) if you haven't already installed the program\).
2. Load all your maps in Tiled which you want to place in a world map.
3. Import the template.tmx file and save it as a new file.
4. Enlarge the size of the former template.
5. Head over to one of your maps which you want to place in the world map.
6.  Click the “Rectangular Select” button that can be found in the menu at the right of the “Eraser” button.
7. Select the “Ground” layer of your map.
8. Drag your mouse from the top left corner to the bottom right corner \(Zoom out if required\).
9. Copy the layer by using Control+C.
10. Paste the layer in the world map at an appropriate place \(Press Control+V\).
11. Keep repeating that procedure for every layer of your map until you have copied the whole map. \(Only the layers “Ground”, “Objects” and “Above” are definitely needed\).
12. Upon pasting your next map, leave one tile of space between the you map you have pasted before. The tile of space isn’t counted as real tile in the worldmap, it just shows the mapchange areas between the maps.
13. If you want to move the maps in your world map, head to Map/Offset Map.
14. You can create an image of the world map by clicking File/Save As Image. WARNING: Images rendered at a high zoom level will be extraordinarily large!.

### Download

The world map can be rebuilt with Tiled as well. This program has actually been used to find out the correct coordinates for the position of the maps in the world map.

You can download the .tmx file from the [Github page](https://github.com/Zukero/andors-trail/blob/master/ProjectPage/maps/worldmap_v.0.7.tmx) \(Click “view raw file” to download it\) 

{% hint style="info" %}
Remember to put your downloaded file into the “xml” folder where all maps are located. On the same level of “xml”, has to be located a “drawable” folder which includes all tilesets used for Andor's Trail.
{% endhint %}



