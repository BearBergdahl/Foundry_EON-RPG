# Strid Integration - Testing Checklist

This document provides a comprehensive testing checklist for verifying the Strid module integration works correctly.

## Pre-Testing Setup

- [ ] Have Foundry VTT installed (v12 or v13)
- [ ] Have the EON RPG system installed
- [ ] Have GM (Game Master) access to the world
- [ ] Create a backup of your world before testing (optional but recommended)

## Test 1: Default Behavior (Basic Mode)

### Goal: Verify system works with default "grund" (basic) setting

1. [ ] Create a new world or use existing world
2. [ ] Verify setting is set to "Nej" (No) by default
   - Navigate to: *⚙️ → Configure Settings → System Settings → Bokinställningar*
   - Check that "Strid" is set to "Nej"
3. [ ] Create a new melee weapon (Närstridsvapen)
   - Should use basic weapon properties
4. [ ] Create a new ranged weapon (Avståndsvapen)
   - Should use basic weapon properties
5. [ ] Verify combat functions work normally
6. [ ] Check console (F12) for any errors

**Expected Result**: System operates normally with basic weapon data

## Test 2: Enable Strid Module

### Goal: Verify Strid can be enabled and loads correctly

1. [ ] Navigate to Book Settings (Bokinställningar)
2. [ ] Change "Strid" setting from "Nej" to "Ja"
3. [ ] Click "Save Changes"
4. [ ] Reload Foundry (F5 or close/reopen browser)
5. [ ] Verify no console errors appear
6. [ ] Check that `CONFIG.EON.settings.bookCombat === true` in console

**Expected Result**: Setting changes successfully and page reloads without errors

## Test 3: Strid Weapons

### Goal: Verify Strid weapon data is loaded

1. [ ] With Strid enabled, open a compendium
2. [ ] Create a new weapon from the Närstridsvapen compendium
3. [ ] Verify weapon has extended properties (if applicable)
4. [ ] Create a new weapon from the Avståndsvapen compendium
5. [ ] Check weapon properties match Strid data
6. [ ] Test weapon in combat (optional but recommended)

**Expected Result**: Weapons use extended Strid data

## Test 4: Toggle Between Modes

### Goal: Verify switching between modes works correctly

1. [ ] Switch from "Ja" to "Nej" in settings
2. [ ] Reload Foundry
3. [ ] Create new weapons - should use basic data
4. [ ] Switch back to "Ja"
5. [ ] Reload Foundry
6. [ ] Create new weapons - should use Strid data
7. [ ] Check existing weapons in inventory (should remain unchanged)

**Expected Result**: System switches between modes cleanly

## Test 5: Data Integrity

### Goal: Verify data structures are correct

### In Browser Console (F12 → Console tab):

```javascript
// Test 1: Check if weapon data exists
console.log("Melee weapons:", game.EON.narstridsvapen);
console.log("Ranged weapons:", game.EON.avstandsvapen);

// Test 2: Check setting value
console.log("Strid enabled:", CONFIG.EON.settings.bookCombat);

// Test 3: Check if egenskaper (properties) exist
console.log("Weapon properties:", game.EON.egenskaper);
```

**Expected Results**:
- [ ] `game.EON.narstridsvapen` contains weapon data
- [ ] `game.EON.avstandsvapen` contains weapon data
- [ ] `CONFIG.EON.settings.bookCombat` is boolean
- [ ] `game.EON.egenskaper` contains weapon properties

## Test 6: Multiplayer Compatibility

### Goal: Verify setting works for all users (if testing multiplayer)

1. [ ] As GM, set Strid to "Ja"
2. [ ] Have players join the world
3. [ ] Players should see/use Strid weapon data
4. [ ] Switch to "Nej" and have players reload
5. [ ] Players should see/use basic weapon data

**Expected Result**: All users respect the GM's setting

## Test 7: Existing Campaigns

### Goal: Verify compatibility with existing save games

1. [ ] Open an existing campaign/world
2. [ ] Enable Strid
3. [ ] Verify existing actors and items still work
4. [ ] Create new items - should use Strid data
5. [ ] Existing items should remain unchanged

**Expected Result**: No data loss, existing items work normally

## Test 8: Error Handling

### Goal: Verify system handles edge cases

1. [ ] Check console (F12) for errors during:
   - [ ] Initial world load
   - [ ] Changing settings
   - [ ] Creating weapons
   - [ ] Combat rolls
2. [ ] Try rapid switching between modes
3. [ ] Verify no memory leaks or performance issues

**Expected Result**: No console errors, smooth operation

## Test 9: Documentation Verification

### Goal: Verify documentation is accurate

1. [ ] Follow steps in STRID_QUICK_START.md
   - [ ] Can find settings as described
   - [ ] Instructions are clear and accurate
2. [ ] Review STRID_INTEGRATION.md
   - [ ] Technical details match implementation
3. [ ] Check README.md
   - [ ] Feature is properly described

**Expected Result**: Documentation is accurate and helpful

## Known Limitations

Document any discovered limitations here:
- Existing weapons in inventories don't auto-update (by design)
- Requires page reload after changing setting (Foundry limitation)
- Only GM can change the setting (expected behavior)

## Regression Testing

After any updates, verify:
- [ ] Basic weapon creation still works
- [ ] Strid weapon creation still works
- [ ] Combat rolls function correctly
- [ ] No new console errors
- [ ] Setting toggle still works

## Reporting Issues

If tests fail, document:
1. **Test Number**: Which test failed
2. **Steps to Reproduce**: Exact steps taken
3. **Expected Result**: What should have happened
4. **Actual Result**: What actually happened
5. **Console Errors**: Any errors from F12 console
6. **Environment**: Foundry version, browser, OS

## Success Criteria

Integration is successful if:
- ✅ All tests pass
- ✅ No console errors during normal operation
- ✅ System works with both "grund" and "strid" modes
- ✅ Toggle between modes works reliably
- ✅ Documentation is accurate
- ✅ No breaking changes to existing functionality

---

**Testing Status**: 🟡 Not yet tested

**Tester Name**: _________________

**Test Date**: _________________

**Foundry Version**: _________________

**Overall Result**: ⬜ Pass / ⬜ Fail / ⬜ Partial
