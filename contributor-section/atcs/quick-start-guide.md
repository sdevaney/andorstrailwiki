# Quick Start Guide

### Overview <a href="#overview" id="overview"></a>

This guide provides step-by-step instructions for creating content for Andor's Trail using ATCS (Andor's Trail Content Studio).

### Prerequisites <a href="#prerequisites" id="prerequisites"></a>

1. **ATCS Installation**: Download and install ATCS from the official [forums](https://andorstrail.com/)
2. **Game Source Code**: Download the complete [source code](https://github.com/AndorsTrailRelease/andors-trail).
3. [**Tiled Map Editor**](https://mapeditor.org/): Install for map creation (optional but recommended).
4. **Java Runtime Environment**: Version 7 or later.

### Setting Up Your First Project <a href="#setting-up-your-first-project" id="setting-up-your-first-project"></a>

### Step 1: Create a Workspace

1. Create a new folder called `atcs_workspace` on your computer.
2. Launch ATCS (run as Administrator on Windows first time).
3. When prompted, select your workspace folder.

### Step 2: Create a Project

1. Go to **File → Create project...**
2. Enter a project name (use lowercase with underscores, e.g., `my_first_content`).
3. Click **Browse...** for "AT Source" and navigate to the `AndorsTrail` subfolder of your downloaded source code.
4. Click **OK** to create the project.
5. Wait for ATCS to load all game data (this may take a few minutes).

### Creating Your First Item <a href="#creating-your-first-item" id="creating-your-first-item"></a>

### Simple Weapon Example

1. In the project tree, right-click on **Items.**
2. Select **Create new → Item.**
3. Fill in the basic information:
   * **ID**: `my_iron_sword` (must be unique)
   * **Name**: `Iron Sword`
   * **Description**: `A well-crafted iron sword`
   * **Category**: Select `weapon_sword` from the dropdown
4. Configure the weapon stats:
   * **Attack Damage Min**: `8`
   * **Attack Damage Max**: `12`
   * **Attack Chance Bonus**: `5`
5. Set the icon:
   * **Icon ID**: Browse existing icons or use `items_weapons_sword_iron`
6. Save the item.

### Consumable Item Example

1. Create new item with ID: `healing_herb`
2. Set **Has Use** to `true`
3. Configure use effect:
   * **HP Reward Min**: `15`
   * **HP Reward Max**: `20`
4. Set the appropriate icon and description.

### Creating NPCs and Monsters <a href="#creating-npcs-and-monsters" id="creating-npcs-and-monsters"></a>

### Basic Monster

1. Right-click **NPCs** in the project tree.
2. Select **Create new → NPC**
3. Fill in basic information:
   * **ID**: `forest_wolf`
   * **Name**: `Forest Wolf`
   * **Icon ID**: `monsters_wolf` (or similar)
4. Configure combat stats:
   * **Max HP**: `35`
   * **Attack Chance**: `65`
   * **Attack Damage Min**: `4`
   * **Attack Damage Max**: `8`
   * **Block Chance**: `15`
5. Set behavior:
   * **Hostile to Player**: `true`
   * **Faction**: `monsters`
6. Configure drops:
   * Create or select an existing droplist.
   * Set experience reward: `25`

### Friendly NPC

1. Create an NPC with an appropriate name and icon.
2. Set **Hostile to Player** to `false`
3. Create dialogue (see dialogue section below)
4. Reference dialogue ID in NPC configuration

### Creating Dialogues <a href="#creating-dialogues" id="creating-dialogues"></a>

### Simple Shop Dialogue

1. Right-click **Dialogues** in the project tree.
2. Create new dialogue with ID: `shopkeeper_basic`
3. Add dialogue phrases:
   * **ID**: `0` (starting phrase)
   * **Text**: `"Welcome to my shop! What can I do for you?"`
   * Add reply options:
     * `"I'd like to buy something"` → leads to shop interface
     * `"Just looking around"` → leads to phrase ID `1`
4. Create additional phrases for different conversation paths.
5. Configure the shop list if creating a trader.

### Creating Quests <a href="#creating-quests" id="creating-quests"></a>

### Basic Fetch Quest

1. Right-click **Quests** in the project tree.
2. Create a new quest with ID: `herb_collection`
3. Set basic info:
   * **Name**: `Herb Collection`
   * **Description**: `Gather healing herbs for the village healer`
4. Configure quest stages:
   * **Stage 10**: `"I need to find 5 healing herbs for the healer"`
   * **Stage 20**: `"I've collected the herbs. Time to return to the healer"`
   * **Stage 100**: `"The healer was grateful for the herbs"` (completion)
5. Set requirements for stage progression:
   * Stage 20 requires: 5x `healing_herb` items
   * Stage 100 rewards: Experience and gold.

### Map Creation with Tiled <a href="#map-creation-with-tiled" id="map-creation-with-tiled"></a>

### Basic Outdoor Map

1. Open Tiled Map Editor
2. Create new map: 32x32 tile size, 20x15 map size.
3. Load existing AT tilesets from the `drawable` folder.
4. Create layers in this order:
   * **Ground**: Base terrain
   * **Objects**: Decorations and items
   * **Above**: Overhanging elements
   * **Walkable**: Mark impassable areas.
5. Add object layers:
   * **Spawn Areas**: For monster placement.
   * **Map Changes**: For exits to other maps.
   * **Signs**: For readable text.

### Object Configuration

**Spawn Areas**:

* Name: `forest_wolf` (matches your NPC ID)
* Type: `spawn`
* Properties: `quantity = 2`, `active = true`

**Map Changes**:

* Name: destination map ID
* Type: `mapchange`
* Properties: destination coordinates

### Testing Your Content <a href="#testing-your-content" id="testing-your-content"></a>

### Export and Test

1. In ATCS, go to **File → Export package generation**
2. Create a zip file with your content.
3. Extract to the game's source directory.
4. Build and run the game to test.

### Debugging Tips

1. Check the Android LogCat for errors.
2. Verify all referenced IDs exist.
3. Test item acquisition and use.
4. Verify NPC dialogue flows.
5. Check quest progression logic.

### Advanced Features <a href="#advanced-features" id="advanced-features"></a>

### Using Scripts

1. Create scripts in the `/res/raw/` folder.
2. Reference scripts in the item or NPC JSON.
3. Example healing potion script:

```javascript
javascript"healing_potion_script" item.onUse [
    if (item.id == "healing_potion") {
        player.hp.cur = player.hp.cur + 25;
    }
]
```

### Complex Quests

* Use conditional dialogue based on quest progress.
* Create branching storylines.
* Implement time-based or location-based triggers.
* Chain multiple quests together.

### Map Integration

1. Update worldmap coordinates.
2. Create logical connections between areas.
3. Add appropriate environmental storytelling.
4. Balance monster spawns and difficulty.

### Content Guidelines <a href="#content-guidelines" id="content-guidelines"></a>

### Naming Conventions

* Use lowercase with underscores for IDs.
* Descriptive but concise names.
* Avoid special characters.
* Maintain consistency with existing content.t

### Balance Considerations

* Items should fit the progression curve.
* NPCs should have appropriate difficulty.
* Rewards should match the effort required.
* Test with different character levels

### Quality Standards

* All text should be proofread.
* Graphics should match the game art style.
* Test all functionality thoroughly.
* Ensure content integrates smoothly.

### Getting Help <a href="#getting-help" id="getting-help"></a>

1. **Official Forums**: Post questions and get community help.
2. **Discord**: Real-time assistance from developers and the community.
3. **Wiki**: Reference existing documentation.
4. **Examples**: Study existing game content for patterns.

### Submission Process <a href="#submission-process" id="submission-process"></a>

1. **Test Thoroughly**: Ensure content works correctly.
2. **Export Package**: Create a clean ATCS export.
3. **Document Changes**: List new content and features.
4. **Submit to Forums**: Post with a detailed description.
5. **Respond to Feedback**: Address reviewer comments.

### Common Mistakes to Avoid <a href="#common-mistakes-to-avoid" id="common-mistakes-to-avoid"></a>

* Forgetting to set item categories correctly.
* Creating unbalanced combat encounters.
* Missing required fields in JSON.
* Inconsistent naming conventions.
* Not testing quest completion paths.
* Creating orphaned content (unreachable areas/items).

This guide should get you started with content creation. Remember that the Andor's Trail community is welcoming and helpful—don't hesitate to ask questions and share your creations!
