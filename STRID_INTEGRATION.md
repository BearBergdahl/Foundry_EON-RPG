# Strid Module Integration

## Overview
The Strid module has been integrated into the Foundry EON-RPG system. This module provides extended combat rules and weapon data from the "Strid" supplement book for the EON RPG system.

## How to Enable Strid Module

The Strid module can be enabled through the system settings:

1. As a GM, go to the Game Settings
2. Navigate to System Settings → Bokinställningar (Book Settings)
3. Find the "Strid" setting
4. Select "Ja" (Yes) to enable Strid rules and data
5. Select "Nej" (No) to use the basic/core rules

## What Changes When Strid is Enabled

When the Strid module is enabled:
- **Weapon Data**: The system uses extended weapon data from `packs/strid.js` instead of the basic `packs/vapen.js`
- **Combat Rules**: Additional combat mechanics and rules from the Strid book become available
- **Body Parts**: Combat targeting uses the Strid body part system (if defined)

## Technical Implementation

### Files Modified
- `module/settings.js`: Enabled the "strid" choice in bookCombat setting
- `module/templates.js`: Changed from hardcoded `harStrid = false` to dynamic setting check

### Data Files
- `packs/strid.js`: Contains extended weapon properties and combat data
- `packs/vapen.js`: Contains basic weapon data (used when Strid is disabled)

### Configuration
The setting is stored in:
```javascript
game.settings.get("eon-rpg", "bookCombat")
```
Values: `"strid"` (enabled) or `"grund"` (basic/disabled)

## Default Behavior
By default, the system uses `"grund"` (basic rules) to maintain compatibility with existing campaigns. Game masters can switch to "strid" mode at any time through the settings menu.

## Note
The Strid module data is already included in the system files (`packs/strid.js`). No additional downloads or installations are required - you just need to enable it in the settings.
