# Strid Module Integration - Summary of Changes

## Changes Made

### 1. Settings Configuration (`module/settings.js`)
**Line 67-78**: Enabled the Strid book option in game settings

**Before:**
```javascript
default: "Nej",
choices: {
    //"strid": "Ja",  // <-- This was commented out
    "grund": "Nej"
}
```

**After:**
```javascript
default: "grund",
choices: {
    "strid": "Ja",   // <-- Now enabled
    "grund": "Nej"
}
```

### 2. Dynamic Data Loading (`module/templates.js`)
**Line 76-79**: Changed from hardcoded flag to dynamic setting check

**Before:**
```javascript
export async function Setup() {
    try {      
        const harStrid = false;  // <-- Hardcoded to false
```

**After:**
```javascript
export async function Setup() {
    try {      
        // Check if Strid module is enabled in settings
        const harStrid = game.settings.get("eon-rpg", "bookCombat") === "strid";
```

### 3. Documentation (`STRID_INTEGRATION.md`)
Added comprehensive documentation explaining:
- How to enable/disable the Strid module
- What changes when Strid is enabled
- Technical implementation details
- Default behavior

## How It Works

```
┌──────────────────────┐
│  Game Settings       │
│  bookCombat setting  │
│  - "strid" (Ja)      │
│  - "grund" (Nej)     │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│  templates.js        │
│  Setup() function    │
│  checks setting      │
└──────────┬───────────┘
           │
     ┌─────┴─────┐
     │           │
     ▼           ▼
┌─────────┐  ┌──────────┐
│ vapen.js│  │strid.js  │
│ (basic) │  │(extended)│
└─────────┘  └──────────┘
     │           │
     └─────┬─────┘
           │
           ▼
    ┌──────────────┐
    │ game.EON.*   │
    │ weapon data  │
    └──────────────┘
```

## Data Structure Compatibility

Both `vapen.js` and `strid.js` export the same structure:
```javascript
{
    "egenskaper": { ... },      // Weapon properties
    "narstridsvapen": { ... },  // Melee weapons
    "avstandsvapen": { ... },   // Ranged weapons
    "forsvar": { ... }          // Defense options
}
```

This ensures seamless switching between the two datasets.

## No Breaking Changes

- Default behavior remains unchanged (`"grund"` is still the default)
- All existing code paths work identically
- The `game.EON.narstridsvapen` and `game.EON.avstandsvapen` references remain valid
- No migration or data conversion needed

## Testing Recommendations

1. **Basic Test**: Load a world with default settings (should use basic weapon data)
2. **Strid Test**: Enable Strid in settings, reload, verify extended weapon data loads
3. **Toggle Test**: Switch between Strid and basic mode multiple times
4. **Combat Test**: Create weapons and test combat with both settings

## Future Enhancements

If the Strid book includes different body part rules:
- Add `strid` section to `eon.kroppsdelar` in `module/config.js`
- Define corresponding `kroppsdelsfaktor` values for Strid mode
