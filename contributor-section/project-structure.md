# Project Structure

### Repository Organization

The main repository contains several key directories:

```
textandors-trail/
├── AndorsTrail/           # Main game source code
│   ├── app/               # Android application module
│   ├── src/               # Java source files
│   └── res/               # Android resources
│       ├── drawable/      # Graphics and tilesets
│       ├── raw/           # Script files (.ats)
│       ├── values/        # Configuration files
│       └── xml/           # Map files (.tmx)
├── AndorsTrailEdit/       # Legacy content editor (deprecated)
└── travis/                # CI/CD scripts
```

### Key Directories

### `/AndorsTrail/res/`

* **`drawable/`**: Contains all game graphics, tilesets, and sprites
* **`xml/`**: TMX map files created with Tiled
* **`raw/`**: Script files (.ats format) for game logic
* **`values/`**: Configuration arrays and resource definitions
* **`layout/`**: Android UI layout files

### Source Code Structure

* **Main Activity**: Game entry point and Android lifecycle management
* **Game Engine**: Core game logic, turn-based combat, map rendering
* **Content Loaders**: JSON and TMX file parsers
* **UI Components**: Inventory, dialogue, combat interfaces

### Game Data Formats <a href="#game-data-formats" id="game-data-formats"></a>

### JSON Structure

Andor's Trail uses JSON files for most game content, stored in the game's resource files.

### Common JSON Fields

```json
json{
  "id": "unique_identifier",
  "name": "Display Name",
  "description": "Player-visible description",
  "category": "content_category"
}
```

### Items JSON Format

```json
json{
  "id": "example_sword",
  "name": "Example Sword",
  "description": "A finely crafted sword",
  "category": "weapon_sword",
  "iconID": "items_weapons_sword_example",
  "equipEffect": {
    "addedAD": {"min": 5, "max": 8},
    "addedAC": 10,
    "addedBC": 5
  },
  "hasUse": false,
  "useType": "weapon",
  "scripts": [],
  "private_scripts": []
}
```

### NPCs/Monsters JSON Format

```json
json{
  "id": "example_goblin",
  "name": "Goblin Warrior",
  "iconID": "monsters_goblin_warrior",
  "spawnGroup": "goblin_group",
  "attackChance": 70,
  "attackDamage": {"min": 3, "max": 6},
  "blockChance": 20,
  "maxHP": 25,
  "maxAP": 10,
  "moveCost": 10,
  "dropList": "goblin_drops",
  "faction": "monsters",
  "hostileToPlayer": true
}
```

### Quest JSON Format

```json
json{
  "id": "example_quest",
  "name": "The Lost Artifact",
  "description": "Find the ancient artifact",
  "stages": [
    {
      "progress": 10,
      "logText": "I need to find the lost artifact.",
      "requirements": []
    },
    {
      "progress": 20,
      "logText": "I found clues about the artifact's location.",
      "requirements": [{"requireType": "item", "id": "ancient_clue", "quantity": 1}]
    }
  ],
  "showInQuestLog": true
}
```

### TMX Map Format

Maps use the Tiled TMX format with specific layer conventions:

### Required Layers

* **Ground**: Base terrain tiles
* **Objects**: Interactive elements, decorations
* **Above**: Elements that render above the player
* **Walkable**: Collision detection (filled tiles are non-walkable)

### Object Layers

* **Spawn Areas**: Monster and NPC placement
* **Map Changes**: Transitions between maps
* **Signs**: Readable text objects
* **Key Areas**: Special interaction zones
