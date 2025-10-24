---
description: All about Andor's Trail Content Studio
---

# ATCS

{% embed url="https://andorstrail.com/viewtopic.php?f=6&t=4806" %}

### ATCS (Andor's Trail Content Studio)

ATCS is the primary tool for content creation, providing a visual editor for all game content types.

### Installation

1. **System Requirements**:
   * Java Runtime Environment 7 or later
   * Windows, macOS, or Linux
   * Recommended: 1GB RAM (increase MAX\_MEM to 1 GB for large projects)
2. **Download and Setup**:
   * Download the latest ATCS release from the forums.
   * Windows: Use the installer executable
   * Linux/macOS: Extract the zip file and make ATCS.sh executable
3. **First Launch Configuration**:
   * Run as Administrator on Windows for the first launch.
   * Create a workspace directory (e.g., "atcs\_workspace")
   * Configure external tools (Tiled for maps, image editor)
   * Set up internet access for translations if needed

### Workspace and Projects

**Workspace**: Central folder where ATCS stores all working data and settings.

**Project Creation**:

1. File → Create project...
2. Enter a meaningful project name (lowercase with underscores)
3. Browse to the "AndorsTrail" subfolder of the game source
4. ATCS will load and validate the game data

### Content Types

ATCS can create and edit:

* **Items**: Weapons, armor, consumables, quest items
* **NPCs**: Monsters, friendly characters, traders
* **Quests**: Multi-stage quest chains with dialogue
* **Dialogues**: Conversation trees and interactions
* **Actor Conditions**: Status effects, buffs, debuffs
* **Droplists**: Item drop configurations
* **World Maps**: Regional map layouts
* **Map Objects**: Spawn areas, signs, map transitions

### Export and Integration

* **Export Package Generation**: Creates zip files with all modified content
* **Content Validation**: Built-in checks for data consistency and references
