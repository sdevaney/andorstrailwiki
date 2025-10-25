---
description: Andor's Trail Scripting Language
---

# ATS

AT (Andor's Trail) Scripting Language is a simple, C-like language used to write scripts (.ats files) that define game logic, trigger events, and control interactive elements in Andor's Trail.

Script files are located in the res/raw/ folder of the project, as plain-text .ats files. The file extension used doesn't matter, but it helps for identification. ATS stands for Andor's Trail Script. There is a detailed breakdown by Zukero on [the forums](https://andorstrail.com/viewtopic.php?t=4342).

### Overview <a href="#overview" id="overview"></a>

AT scripts are stored in `res/raw/` as `.ats` files and are executed by the game engine in response to triggers like:

* Map entry/exit
* Player actions
* NPC interactions
* Combat events
* Item usage

Scripts define behavior through **associations** - connections between game objects and script methods.

### Basic Script Structure <a href="#basic-script-structure" id="basic-script-structure"></a>

```
textassociation MyAssociation {
    onCondition() {
        // Triggered when condition is met
    }
    
    onExecute() {
        // Main execution logic
    }
    
    onDeactivate() {
        // Cleanup when association ends
    }
}
```

### Script Lifecycle <a href="#script-lifecycle" id="script-lifecycle"></a>

1. **onLoad** - Script file is loaded into memory.
2. **onInstantiate** - Association object is created.
3. **onActivate** - Condition is met, association becomes active.
4. **onExecute** - Main logic runs each game tick.
5. **onDeactivate** - Association becomes inactive or is destroyed.

### Variables and Types <a href="#variables-and-types" id="variables-and-types"></a>

### Variable Declaration

```
text// Numerals (integers)
numeral myCounter = 0;
numeral damage = 10;

// Booleans
boolean isActive = true;
boolean hasItem = false;

// Strings
string dialogueText = "Hello, adventurer!";
string npcName = "Merchant";
```

### Value Types

* **numeral**: Integer values (-∞ to +∞)
* **boolean**: true or false.
* **string**: Text values enclosed in quotes.
* **association**: Reference to another association.
* **actor**: Reference to an NPC or monster.

### Trigger Conditions <a href="#trigger-conditions" id="trigger-conditions"></a>

Conditions determine when an association activates:

### Map Triggers

```
textassociation OnMapEntry {
    onCondition() {
        // Triggered when player enters the map
        return map.onEnter();
    }
    
    onExecute() {
        // Show welcome dialogue
        npc.say("Welcome!");
    }
}
```

### Player Triggers

```
textassociation OnPlayerDeath {
    onCondition() {
        return player.onKilled();
    }
    
    onExecute() {
        // Handle death
    }
}

association OnPlayerLevelUp {
    onCondition() {
        return player.onGainLevel();
    }
}
```

### NPC Triggers

```
textassociation OnNPCKilled {
    onCondition() {
        return npc.onKilled();
    }
}

association OnNPCSpoken {
    onCondition() {
        return npc.onSpoken();
    }
}
```

### Item Triggers

```
textassociation OnItemPickup {
    onCondition() {
        return player.onPickupItem("item_id");
    }
}

association OnItemUse {
    onCondition() {
        return player.onUseItem("item_id");
    }
}
```

### Control Flow <a href="#control-flow" id="control-flow"></a>

### If-Else Statements

```
textassociation CheckPlayerHealth {
    onExecute() {
        if (player.getHP() < 10) {
            player.say("I'm badly wounded!");
        } else if (player.getHP() < 50) {
            player.say("I'm injured.");
        } else {
            player.say("I'm healthy.");
        }
    }
}
```

### While Loops

```
textassociation CounterLoop {
    numeral count = 0;
    
    onExecute() {
        while (count < 10) {
            // Perform action
            count = count + 1;
        }
    }
}
```

### Logical Operators

```
textif (condition1 AND condition2) {
    // Both must be true
}

if (condition1 OR condition2) {
    // Either can be true
}

if (NOT condition) {
    // Condition must be false
}
```

### Method Calls <a href="#method-calls" id="method-calls"></a>

### Player Methods

```
textplayer.getHP()              // Get current HP
player.getMaxHP()           // Get maximum HP
player.getAP()              // Get action points
player.getLevel()           // Get current level
player.hasItem("item_id")   // Check if player has item
player.addItem("item_id")   // Add item to inventory
player.removeItem("item_id") // Remove item from inventory
player.say("text")          // Display dialogue
player.moveNorth()          // Move player north
player.moveSouth()          // Move player south
player.moveEast()           // Move player east
player.moveWest()           // Move player west
```

### NPC Methods

```
textnpc.say("text")             // NPC says text
npc.getHP()                 // Get NPC health
npc.getLevel()              // Get NPC level
npc.moveToPlayer()          // NPC moves toward player
npc.moveAway()              // NPC moves away from player
npc.attack(player)          // NPC attacks player
npc.die()                   // NPC dies
```

### Map Methods

```
textmap.changeMap("map_id")     // Change to another map
map.spawnMonster("id")      // Spawn a monster
map.despawnMonster("id")    // Remove a monster
map.displayMessage("text")  // Show message to player
```

### Item Methods

```
textitem.getID()                // Get item ID
item.getName()              // Get item name
item.getDescription()       // Get item description
item.getQuantity()          // Get quantity in inventory
```

### Associations <a href="#associations" id="associations"></a>

Associations link script logic to game objects and events:

### Association Types

```
text// NPC Association
association NPCGreeting {
    npc merchantName;
    
    onCondition() {
        return merchantName.onSpoken();
    }
    
    onExecute() {
        merchantName.say("Welcome to my shop!");
    }
}

// Map Association
association TrapTile {
    numeral damageAmount = 10;
    
    onCondition() {
        return player.onEnterTile(15, 20);
    }
    
    onExecute() {
        player.takeDamage(damageAmount);
        map.displayMessage("You stepped on a trap!");
    }
}

// Item Association
association PotionEffect {
    onCondition() {
        return player.onUseItem("health_potion");
    }
    
    onExecute() {
        player.heal(50);
        map.displayMessage("You drank the potion!");
    }
}
```

### State Management <a href="#state-management" id="state-management"></a>

Track state using association variables:

```
textassociation QuestProgress {
    numeral stage = 0;
    boolean hasReward = false;
    
    onExecute() {
        if (stage == 0 AND player.hasItem("quest_item")) {
            stage = 1;
            npc.say("You found the item!");
        }
        
        if (stage == 1 AND NOT hasReward) {
            player.addItem("reward");
            hasReward = true;
            stage = 2;
        }
    }
}
```

### Common Patterns <a href="#common-patterns" id="common-patterns"></a>

### Quest Trigger

```
textassociation QuestStart {
    onCondition() {
        return npc.onSpoken();
    }
    
    onExecute() {
        if (player.getLevel() >= 5) {
            npc.say("Will you help me?");
            // Add quest to player
        } else {
            npc.say("Come back when you're stronger.");
        }
    }
}
```

### Dialogue Progression

```
textassociation Dialogue {
    numeral stage = 0;
    
    onCondition() {
        return npc.onSpoken();
    }
    
    onExecute() {
        if (stage == 0) {
            npc.say("Hello, traveler!");
            stage = 1;
        } else if (stage == 1) {
            npc.say("Have you considered my offer?");
            stage = 2;
        } else {
            npc.say("Farewell!");
        }
    }
}
```

### Conditional Reward

```
textassociation RewardNPC {
    onCondition() {
        return npc.onSpoken();
    }
    
    onExecute() {
        if (player.hasItem("required_item")) {
            player.removeItem("required_item");
            player.addItem("reward_item");
            npc.say("Thank you! Here is your reward.");
        } else {
            npc.say("Do you have what I asked for?");
        }
    }
}
```

### Best Practices <a href="#best-practices" id="best-practices"></a>

1. **Use descriptive names** - Name associations and variables clearly
2. **Keep scripts focused** - One association should handle one logical unit
3. **Check conditions** - Always verify conditions before executing actions
4. **State tracking** - Use variables to track quest/dialogue progress
5. **Error handling** - Assume items or NPCs might not exist
6. **Comments** - Document complex logic
7. **Testing** - Test edge cases (missing items, NPCs, etc.)

### Integration with Game Files <a href="#integration-with-game-files" id="integration-with-game-files"></a>

Scripts are referenced in JSON files:

```json
json{
  "id": "example_npc",
  "name": "Merchant",
  "scripts": ["npc_greeting", "npc_trade"],
  "private_scripts": ["npc_internal_logic"]
}
```

### Limitations <a href="#limitations" id="limitations"></a>

* Scripts run synchronously - they cannot create delays or wait
* Script execution is limited to prevent infinite loops
* Access to game objects is restricted for security
* Cannot directly modify save game data

### Debugging Tips <a href="#debugging-tips" id="debugging-tips"></a>

1. Add dialogue messages to track execution
2. Check console output for script errors
3. Use map.displayMessage() to show variable values
4. Test each association independently
5. Verify JSON references are correct

### Resources <a href="#resources" id="resources"></a>

* Forum Discussion: [AT Scripting Language documentation](https://andorstrail.com/viewtopic.php?t=4342)
* Example Scripts: Check res/raw/\*.ats in game repository
* Game Engine: See source code in src/com/.../ for method definitions
