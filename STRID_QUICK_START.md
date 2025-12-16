# Quick Start: Using the Strid Module

## What is the Strid Module?

The Strid module contains extended combat rules and weapon data from the EON RPG "Strid" supplement book. It provides more detailed weapon properties, combat mechanics, and tactical options.

## Enabling Strid (for Game Masters)

1. **Open Game Settings**
   - Click the gear icon ⚙️ in the toolbar
   - Navigate to "Configure Settings"

2. **Access Book Settings**
   - Go to "System Settings" tab
   - Find and click "Bokinställningar" (Book Settings)

3. **Enable Strid**
   - Locate the "Strid" setting
   - Change from "Nej" (No) to "Ja" (Yes)
   - Click "Save Changes"

4. **Reload Foundry**
   - Press F5 or reload the page for changes to take effect
   - The system will now use extended Strid weapon data

## What Changes?

### When Strid is DISABLED (Default: "Nej")
- Uses basic weapon data from `packs/vapen.js`
- Standard combat rules from the core rulebook
- Simpler weapon properties

### When Strid is ENABLED ("Ja")
- Uses extended weapon data from `packs/strid.js`
- Additional combat tactics and maneuvers
- More detailed weapon properties and combat rules
- Enhanced tactical options for combat

## Visual Indicator

You can check which mode is active by:
1. Opening a weapon item
2. Checking the available properties and options
3. Strid mode will have additional weapon properties and combat mechanics

## Switching Between Modes

You can switch between Strid and basic mode at any time:
1. Change the setting in Book Settings
2. Reload Foundry (F5)
3. All new weapons will use the current mode's data
4. Existing weapons in your inventory remain unchanged unless recreated

## Compatibility

- **Save Games**: Both modes are compatible with existing save games
- **Multiplayer**: All players will use the GM's setting
- **Modules**: The setting is independent of other modules
- **Default**: System defaults to "Nej" (basic mode) for new worlds

## Troubleshooting

### Problem: Setting doesn't appear
**Solution**: You must be logged in as the Game Master to access this setting

### Problem: Changes don't take effect
**Solution**: Reload the page (F5) after changing the setting

### Problem: Existing weapons don't update
**Solution**: The setting affects weapon data loading, not items already in inventories. Create new weapons from the compendium to see the changes.

## Need More Information?

- See `STRID_INTEGRATION.md` for detailed technical information
- See `INTEGRATION_SUMMARY.md` for a summary of code changes
- Check the [GitHub repository](https://github.com/BearBergdahl/Foundry_EON-RPG) for updates

---

*Note: "Strid" and EON RPG content belongs to Helmgast AB. This integration is provided for use with legally obtained materials.*
