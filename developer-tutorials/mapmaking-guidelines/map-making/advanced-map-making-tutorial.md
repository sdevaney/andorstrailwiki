---
description: >-
  This is a tutorial on how to create maps with a higher difficulty level for
  Andor's Trail.
---

# Advanced Map Making Tutorial

1.  Make sure that you have already read the [Map Making](https://andorstrail.com/wiki/test/andors_trail_wiki/developer_section.html) tutorial, the [Map Editor](https://andorstrail.com/wiki/test/andors_trail_wiki/developer_section.html) tutorial and the [Mapmaking Guidelines](https://andorstrail.com/wiki/test/andors_trail_wiki/developer_section/mapmaking_guidelines.html).
2. Now, you are ready to draw a more advanced map!
3. I'm going to draw an outdoor map with three mountains, a lake area, a forest and a hut inhabited by a hermit.
4. As always, the first thing you have to do is defining the size of the map \(30×30 in this case\) and painting the “Ground” layer. In this case I chose the grass tile and painted the whole map using the brush tool.

![](../../../.gitbook/assets/tutorial1.png)

5.  Let's add a lake area in the bottom left hand corner with two small islands. To do that, I switched to the paint tool and selected the ordinary water tile.

![](../../../.gitbook/assets/tutorial2.png)

6.  Mountains add more elevation to the flat map. I start by drawing some grey mountain walls on the top of the map and a brown mountain area to the left and the right. I'm drawing the wall tops as well to make the left hand mountain area visible because it hasn't got any walls for now.

![](../../../.gitbook/assets/tutorial5.png)

7.  Of course, the wall corners shouldn't be missing. Let's add them to the grey and brown area.

![](../../../.gitbook/assets/tutorial6.png)

8.  Now, we can see a rough draft of the map we want to create by using the brush tool again and filling the mountain tops with the grey or brown tile.

![](../../../.gitbook/assets/tutorial7.png)

9.  Let's add some more walls on top of the first mountain level to make it really look like a mountain and not like a flat highland. I recommend differing the base wall height of two tiles like I did in the grey area.

![](../../../.gitbook/assets/tutorial14.png)

10.  To make the edges look even more smoothly, I draw the bottom and top corners which are placed in “Objects”.

![](../../../.gitbook/assets/tutorial15.png)

11.  If I would just draw the top corners over the brown area, the edges wouldn't be very visible and the map may not look perfect. So, I added some small dirt trails at the place where the corners should be. After that, I'm switching to “Above” and draw the edges over the dirt trail. Doesn't it look better now?

![](../../../.gitbook/assets/tutorial16.png)

![](../../../.gitbook/assets/tutorial17.png)

12.  The lake needs some dirt borders as overlay to make the intersection between the lake and the grass tiles look more smoothly. I draw the borders in “Objects”. I usually add the corner tiles at first, then the straight tiles and finally the round which connect the corners with the straight tiles. At this point, I noticed the lake being too straight in the north, so I changed the outline a little bit.

![](../../../.gitbook/assets/tutorial19.png)

![](../../../.gitbook/assets/tutorial22.png)

![](../../../.gitbook/assets/tutorial23.png)

13.  What about a small house in the top right hand corner? Let's switch to the “Ground” layer and draw a dark wooden wall and a greenish wooden roof.

![](../../../.gitbook/assets/tutorial24.png)

![](../../../.gitbook/assets/tutorial25.png)

14. Let's add some windows and a door in “Objects”.

![](../../../.gitbook/assets/tutorial26.png)

![](../../../.gitbook/assets/tutorial27.png)

15.  To improve the intersection between the grass and the lake even more, I'm adding some dirt tiles in “Ground” located in map\_ground\_1 and partially redraw the dirt borders.

![](../../../.gitbook/assets/tutorial28.png)

16.  Now, about the forest. I think, a mixed forest fits the best to this map. I usually fill the area at first with one type of tree \(in this case a deciduous tree type\) and afterwards I remove more and more trees by either creating a path through the forest or by merely overwriting the trees with another type \(e.g. tall trees, coniferous trees or naked trees\). Don't forget to draw the bottom of the tree in “Objects” and the treetop in “Above”.

![](../../../.gitbook/assets/tutorial29.png)

![](../../../.gitbook/assets/tutorial30.png)

![](../../../.gitbook/assets/tutorial31.png)

![](../../../.gitbook/assets/tutorial32.png)

![](../../../.gitbook/assets/tutorial33.png)

![](../../../.gitbook/assets/tutorial34.png)

17.  Finally we' re getting to the small cracks and rocks etc. which give the map the true look. First, I'm fully using the map\_broken\_1 repertoire. All the tiles I'm using can be drawn in “Objects”.

![](../../../.gitbook/assets/tutorial36.png)

18. Hassocks and tree stumps and other small things are also required for a good looking map.

![](../../../.gitbook/assets/tutorial37.png)

19. Let's add some rocks to refine the mountains.

![](../../../.gitbook/assets/tutorial38.png)

20.  What about a dirt pile on the brown mountain area? Let's add that.

![](../../../.gitbook/assets/tutorial39.png)

21.  I drew a few naked trees on top of the mountains to make the map look even more realistic.

![](../../../.gitbook/assets/tutorial40.png)

22. Additionally, I created a camp next to the lake area.

![](../../../.gitbook/assets/tutorial41.png)

![](../../../.gitbook/assets/tutorial42.png)

23. Bridges are necessary but a little bit tricky: The walkway should be drawn in the “Ground” layer and the shadows under it in the “Above” layer.

![](../../../.gitbook/assets/tutorial43.png)

24. I added some crates in front of the hermit's house in “Objects”.

![](../../../.gitbook/assets/tutorial44.png)

25. The house needs some eaves which I add in “Above” because they're similar to shadows.

![](../../../.gitbook/assets/tutorial45.png)

26. Dirt piles and holes look good at the shore. I'm adding them in “Ground”.

![](../../../.gitbook/assets/tutorial46.png)

27. The hermit needs of course a safe place. I did this by adding a fence in “Objects”. He has also stored some firewood under the eave. Some tiles I used aren't displayed. They're located in map\_outdoor\_1.

![](../../../.gitbook/assets/tutorial48.png)

28.  Let's add a small field in “Ground” because the hermit has to live self-sufficient in the wilds. I drew some edible plants over the field in “Objects”.

![](../../../.gitbook/assets/tutorial49.png)

![](../../../.gitbook/assets/tutorial50.png)

29.   Now, to the shadows. The shadows have to follow the shadow rules which I described in the [Map Making](./) tutorial. They're added in “Above”. In the second screenshot, I added a small shadow in “Objects” on the right hand side of the chest. This only needed if the crate tile hasn't already got a shadow.

![](../../../.gitbook/assets/tutorial51.png)

![](../../../.gitbook/assets/tutorial52.png)

30.  We're almost finished with the look of the map. The only thing we have to add is the walkable layer. The purple tiles in the “Walkable“ layer show the areas which are inaccessible. I also removed some trees to make some locations accessible.

![](../../../.gitbook/assets/tutorial81.png)

31.   This really looks like a great map now, doesn't it? But the object layers are still missing \(Mapevents, Spawn, Keys and Replace\). You can do a lot of tricky stuff with the layers what I'm showing now. How to use these layers and create their properties is shown in the [Map Editor](../map-editor.md) tutorial.

32.  At first, I draw the “Mapevents” layer by selecting the “Insert Rectangle” tool and placing several rectangles at the borders of the map. Then, I edited the properties of the object area.

![](../../../.gitbook/assets/tutorial55.png)

![](../../../.gitbook/assets/mapchange.png)

33.  What about a sleeping place in the camp?

![](../../../.gitbook/assets/tutorial56.png)

![](../../../.gitbook/assets/rest.png)

34.  Let's draw a sign in “Objects” to show who the owner of the hut is. I added a “sign” area over it.

![](../../../.gitbook/assets/tutorial58.png)

![](../../../.gitbook/assets/tutorial59.png)

![](../../../.gitbook/assets/sign.png)

39.  I want the barrel to be lootable, so I set its properties as container. I made barrel walkable, so the player has access to the goods.

![](../../../.gitbook/assets/tutorial61.png)

![](../../../.gitbook/assets/container.png)

36.  Traps are really necessary! I drew a swamp in “Ground” and then I created a script area.

![](../../../.gitbook/assets/tutorial63.png)

![](../../../.gitbook/assets/tutorial64.png)

![](../../../.gitbook/assets/script.png)

37.  Monsters are another essential thing in Andor's Trail, so I added a few spawn areas.

![](../../../.gitbook/assets/tutorial66.png)

![](../../../.gitbook/assets/spawn.png)

38.  Let's lock the area to the southeast with a key area.

![](../../../.gitbook/assets/tutorial67.png)

![](../../../.gitbook/assets/key.png)

39.  Then, I added a replace object area by adding the “Replace” layer \(Right click the layer window and create a new object layer\). This can be used to change the look of the map upon meeting the particular requirements. I replaced the door in “Objects” to make it look closed and additionally, I made the whole door unwalkable. I added a new tile layer over “Objects” called “Objects\_changed”. I selected the new layer and drew an open door over the closed one. Then, did the same for “Walkable” and called the new laye r”Walkable\_changed“ and placed a walkable tile over the top of the door. After that, the only thing you need to do is placing a rectangle over the whole door and editing its properties.

![](../../../.gitbook/assets/tutorial69.png)

![](../../../.gitbook/assets/tutorial70.png)

![](../../../.gitbook/assets/tutorial83.png)

![](../../../.gitbook/assets/tutorial78.png)

![](../../../.gitbook/assets/replace.png)

40.   That's it. Map complete. You can download the map from [this](https://github.com/Zukero/andors-trail/blob/master/ProjectPage/advanced_mapmaking_tutorial/tutorial2.tmx) page.

![](../../../.gitbook/assets/tutorial80.png)

## Publishing the Map

To make the map end up as an official map in Andor's Trail, you will need to do the following:  
Make sure the map follows the [Mapmaking Guidelines](../).

Create an issue in the issue tracker on the project page, so people can review the map, post it in the [Andor's Trail forums](https://andorstrails.com) or create a [GitHub](https://github.com/Zukero/andors-trail) pull request with it.

Thank you for reading the tutorial. We look forward to seeing your beautiful maps!

