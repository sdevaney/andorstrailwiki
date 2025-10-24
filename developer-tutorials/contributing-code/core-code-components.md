# Core Code Components

### AndorsTrailApplication.java

Main application entry point and global configuration.

**Debug Parameters:**

```java
javapublic static final boolean DEVELOPMENT_DEBUGRESOURCES = false;
public static final boolean DEVELOPMENT_VALIDATEDATA = false;
public static final boolean DEVELOPMENT_FORCE_DEBUG_BUTTON = false;
```

### Game Engine Structure

**Main Classes:**

* `GameActivity`: Primary game activity and UI controller.
* `GameModel`: Core game state and logic.
* `MapController`: Map rendering and player movement.
* `CombatController`: Turn-based combat system.
* `QuestController`: Quest progression and tracking.
* `InventoryController`: Item management and equipment.

### Resource Loading System

### Content Loaders

**Resource Configuration:**\
Files: `res/values/loadresources.xml` and `res/values/loadresources_debug.xml`

```xml
xml<string-array name="loadresources_items">
    <item>items_weapons</item>
    <item>items_armor</item>
    <item>items_consumables</item>
</string-array>

<string-array name="loadresources_npcs">
    <item>npcs_monsters</item>
    <item>npcs_friendly</item>
</string-array>

<string-array name="loadresources_scripts">
    <item>example_script</item>
</string-array>
```

### JSON Data Loading

**Item Loader Example:**

```java
javapublic class ItemLoader {
    public static void loadItems(Resources resources, ItemDataStore dataStore) {
        String[] itemFiles = resources.getStringArray(R.array.loadresources_items);
        for (String filename : itemFiles) {
            int resourceId = resources.getIdentifier(filename, "raw", packageName);
            InputStream inputStream = resources.openRawResource(resourceId);
            parseItemJson(inputStream, dataStore);
        }
    }
}
```

### Data Structures <a href="#data-structures" id="data-structures"></a>

### Core Game Objects

### Item Class Structure

```java
javapublic class Item {
    public String id;
    public String name;
    public String description;
    public String category;
    public String iconID;
    public ItemType itemType;
    public EquipEffect equipEffect;
    public UseEffect useEffect;
    public boolean hasUse;
    public List<Script> scripts;
    public List<Script> privateScripts;
}

public class EquipEffect {
    public Range addedAD;  // Attack Damage
    public int addedAC;    // Attack Chance
    public int addedBC;    // Block Chance
    public int addedMaxHP;
    public int addedMaxAP;
}
```

### NPC/Monster Structure

```java
javapublic class Monster {
    public String id;
    public String name;
    public String iconID;
    public String spawnGroup;
    public int attackChance;
    public Range attackDamage;
    public int blockChance;
    public int maxHP;
    public int maxAP;
    public int moveCost;
    public String dropList;
    public String faction;
    public boolean hostileToPlayer;
    public List<ActorCondition> conditions;
}
```

### Quest Structure

```java
javapublic class Quest {
    public String id;
    public String name;
    public String description;
    public List<QuestStage> stages;
    public boolean showInQuestLog;
    public String requiredQuestId;
    public int requiredQuestStage;
}

public class QuestStage {
    public int progress;
    public String logText;
    public List<QuestRequirement> requirements;
    public List<QuestReward> rewards;
}
```

### Map System <a href="#map-system" id="map-system"></a>

### TMX Map Loading

### Map Parser Implementation

```java
javapublic class TmxMapLoader {
    public GameMap loadMap(String mapId, Resources resources) {
        int resourceId = resources.getIdentifier(mapId, "xml", packageName);
        XmlResourceParser parser = resources.getXml(resourceId);
        return parseMap(parser);
    }
    
    private GameMap parseMap(XmlResourceParser parser) {
        // Parse TMX XML structure
        // Extract layers, tilesets, object groups
        // Create GameMap object
    }
}
```

### Map Object Types

**Spawn Area:**

```java
javapublic class SpawnArea extends MapObject {
    public String spawnGroup;
    public int quantity = 1;
    public boolean active = true;
    public Rectangle area;
}
```

**Map Change:**

```java
javapublic class MapChange extends MapObject {
    public String destinationMap;
    public Point destinationPosition;
    public Rectangle area;
}
```

### Rendering System

### Layer Rendering Order

1. Ground layer (base terrain).
2. Objects layer (decorations, items).
3. Actors (NPCs, monsters, player).
4. Above layer (overhanging elements).
5. UI elements.

### Tile Rendering

```java
javapublic class MapRenderer {
    public void renderMap(Canvas canvas, GameMap map, ViewPort viewport) {
        renderLayer(canvas, map.groundLayer, viewport);
        renderLayer(canvas, map.objectsLayer, viewport);
        renderActors(canvas, map.actors, viewport);
        renderLayer(canvas, map.aboveLayer, viewport);
    }
}
```

### Combat System <a href="#combat-system" id="combat-system"></a>

### Turn-Based Combat Implementation

### Combat Flow

```java
javapublic class CombatController {
    public enum CombatResult {
        PLAYER_VICTORY,
        PLAYER_DEFEAT,
        COMBAT_CONTINUES
    }
    
    public CombatResult processPlayerAttack(Monster target) {
        AttackResult result = calculateAttack(player, target);
        applyDamage(target, result.damage);
        return checkCombatEnd();
    }
    
    private AttackResult calculateAttack(Actor attacker, Actor defender) {
        boolean hit = (attacker.attackChance >= random.nextInt(100));
        if (!hit) return AttackResult.MISS;
        
        boolean blocked = (defender.blockChance >= random.nextInt(100));
        if (blocked) return AttackResult.BLOCKED;
        
        int damage = attacker.attackDamage.random();
        return new AttackResult(damage);
    }
}
```

### Status Effects (Actor Conditions)

### Actor Condition System

```java
javapublic class ActorCondition {
    public String id;
    public String name;
    public String description;
    public int duration;  // In combat rounds
    public int magnitude;
    public ConditionType type;
    public List<Script> scripts;
}

public enum ConditionType {
    BUFF,
    DEBUFF,
    NEUTRAL
}
```

### Script Engine <a href="#script-engine" id="script-engine"></a>

### ATS Script Implementation

### Script Parser

```java
javapublic class ScriptParser {
    public Script parseScript(String scriptText) {
        // Tokenize script text
        // Build abstract syntax tree
        // Validate syntax and references
        return compiledScript;
    }
}
```

### Script Execution Engine

```java
javapublic class ScriptEngine {
    private Map<String, Object> gameObjects;
    private Map<String, ScriptVariable> localVariables;
    
    public void executeScript(Script script, ScriptContext context) {
        setupGameObjects(context);
        for (Statement statement : script.statements) {
            executeStatement(statement);
        }
    }
    
    private void executeStatement(Statement statement) {
        switch (statement.type) {
            case ASSIGNMENT:
                executeAssignment((AssignmentStatement) statement);
                break;
            case METHOD_CALL:
                executeMethodCall((MethodCallStatement) statement);
                break;
            case IF_ELSE:
                executeConditional((ConditionalStatement) statement);
                break;
            case WHILE_LOOP:
                executeWhileLoop((WhileLoopStatement) statement);
                break;
        }
    }
}
```

### Available Script Methods

**Player Methods:**

```java
java// Inventory management
player.getItemCount(String itemId) -> int
player.giveItem(String itemId, int count)
player.removeItem(String itemId, int count)

// Equipment
player.getItemInSlot(String slot) -> Item
player.equipItemInSlot(String itemId, String slot)
player.unequipSlot(String slot)

// Quest progression
player.hasQuestProgress(String questId, int stage) -> boolean
player.addQuestProgress(String questId, int stage)

// Character progression
player.addExperience(int amount)
player.addAlignment(String factionId, int amount)

// Status effects
player.addActorCondition(String conditionId, int magnitude, int duration, int chance)
player.clearActorCondition(String conditionId)
```

**Map Methods:**

```java
javamap.activateGroup(String groupId)
map.deactivateGroup(String groupId)
world.getMap(String mapId) -> Map
```

### Save System <a href="#save-system" id="save-system"></a>

### Save Data Structure

### Player Save Data

```java
javapublic class PlayerSaveData {
    public int level;
    public int experience;
    public int currentHP;
    public int currentAP;
    public Map<String, Integer> inventory;
    public Map<String, Item> equipment;
    public Map<String, Integer> questProgress;
    public Map<String, Integer> alignments;
    public List<ActorCondition> conditions;
    public String currentMap;
    public Point position;
}
```

### Save/Load Implementation

```java
javapublic class SaveGameManager {
    public void saveGame(PlayerSaveData saveData, String filename) {
        Gson gson = new Gson();
        String json = gson.toJson(saveData);
        writeToFile(json, filename);
    }
    
    public PlayerSaveData loadGame(String filename) {
        String json = readFromFile(filename);
        Gson gson = new Gson();
        return gson.fromJson(json, PlayerSaveData.class);
    }
}
```

### Performance Considerations <a href="#performance-considerations" id="performance-considerations"></a>

### Memory Management

### Object Pooling for Frequent Allocations

```java
javapublic class ObjectPool<T> {
    private List<T> available = new ArrayList<>();
    private ObjectFactory<T> factory;
    
    public T acquire() {
        if (available.isEmpty()) {
            return factory.create();
        }
        return available.remove(available.size() - 1);
    }
    
    public void release(T object) {
        resetObject(object);
        available.add(object);
    }
}
```

### Resource Management

* Use `Resources.openRawResource()` for JSON files.
* Cache parsed data structures.
* Recycle bitmaps when possible.
* Use efficient data structures (HashMap for lookups).

### Rendering Optimization

### Viewport Culling

```java
javapublic class ViewPort {
    public Rectangle visibleArea;
    
    public boolean isVisible(Rectangle objectBounds) {
        return visibleArea.intersects(objectBounds);
    }
}
```

### Sprite Batching

* Group similar sprites for batch rendering.
* Use sprite sheets instead of individual images.
* Minimize texture switches during rendering.

### Testing Framework <a href="#testing-framework" id="testing-framework"></a>

### Unit Testing

### Test Structure

```java
java@RunWith(AndroidJUnit4.class)
public class ItemLoaderTest {
    @Test
    public void testItemLoading() {
        Context context = InstrumentationRegistry.getTargetContext();
        ItemDataStore dataStore = new ItemDataStore();
        ItemLoader.loadItems(context.getResources(), dataStore);
        
        assertTrue("Items should be loaded", dataStore.size() > 0);
        assertNotNull("Specific item should exist", dataStore.getItem("iron_sword"));
    }
}
```

### Integration Testing

### Combat System Tests

```java
javapublic class CombatControllerTest {
    @Test
    public void testPlayerVictory() {
        Player player = createTestPlayer();
        Monster weakMonster = createWeakMonster();
        
        CombatController combat = new CombatController();
        CombatResult result = combat.fight(player, weakMonster);
        
        assertEquals(CombatResult.PLAYER_VICTORY, result);
    }
}
```

### Build Configuration <a href="#build-configuration" id="build-configuration"></a>

### Gradle Build Script

### Dependencies

```
textdependencies {
    implementation 'com.google.code.gson:gson:2.8.6'
    implementation 'androidx.appcompat:appcompat:1.2.0'
    testImplementation 'junit:junit:4.13.2'
    androidTestImplementation 'androidx.test:runner:1.3.0'
}
```

### Build Types

```
textbuildTypes {
    debug {
        debuggable true
        applicationIdSuffix ".debug"
        versionNameSuffix "-debug"
    }
    
    release {
        minifyEnabled true
        proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
        signingConfig signingConfigs.release
    }
}
```

### API Compatibility <a href="#api-compatibility" id="api-compatibility"></a>

### Minimum Android Version

* **API Level**: 35 (Android 15).
* **Target API**: Latest stable Android version.
* **Architecture**: ARMv7, ARM64, x86.

### Backwards Compatibility

* Avoid newer API features without compatibility checks.
* Use support libraries for modern UI components.
* Test on minimum API level devices.

### Security Considerations <a href="#security-considerations" id="security-considerations"></a>

### Save Game Integrity

* Validate the saved data structure.
* Check for impossible values.
* Prevent save game tampering.

### Content Validation

* Validate all loaded content for required fields.
* Check references to other game objects.
* Prevent script injection attacks.

### Debugging Tools <a href="#debugging-tools" id="debugging-tools"></a>

### LogCat Integration

```java
javapublic class GameLog {
    private static final String TAG = "AndorsTrail";
    
    public static void debug(String message) {
        if (BuildConfig.DEBUG) {
            Log.d(TAG, message);
        }
    }
    
    public static void error(String message, Throwable throwable) {
        Log.e(TAG, message, throwable);
    }
}
```

### Development Cheats

```java
javaif (DEVELOPMENT_DEBUGRESOURCES) {
    // Enable god mode
    // Fast level progression
    // Item spawning
    // Map teleportation
}
```

This technical reference provides the foundation for understanding and extending Andor's Trail codebase. For specific implementation details, refer to the source code and existing patterns within the project.
