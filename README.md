# PSYCHRONIC_GamepadConfigMZ

**RPG Maker MZ Plugin**

Customize gamepad controls with a visual controller interface

## What It Does

This plugin allows players to customize their gamepad controls from the Options menu. It features a visual gamepad diagram where players can click on buttons to assign actions. Both Standard and Alternative layouts are supported by default.

## Plugin File

- `PSYCHRONIC_GamepadConfigMZ.js`
- Version: `1.0.5`
- Target: RPG Maker MZ
- Author: Psychronic
- URL: https://psychronic.itch.io

## Parameter Summary

- commandName: The name shown in the Options menu
- buttonHelp: Help text shown when hovering over a button
- defaultHelp: Help text for the Default Layout option
- altHelp: Help text for the Alternative Layout option
- finishHelp: Help text for the Finish option
- assignedColor: Background color for buttons with actions assigned
- selectedColor: Background color for currently selected button
- protectedColor: Background color for protected (locked) buttons
- actionColor: Text color for action names on buttons
- clearText: Text for clearing a button assignment
- okKey: Short text shown on the button
- okText: Full text shown in action selection
- escapeKey: Short text shown on the button
- escapeText: Full text shown in action selection
- menuKey: Short text shown on the button
- menuText: Full text shown in action selection
- shiftKey: Short text shown on the button
- shiftText: Full text shown in action selection
- pageupKey: Short text shown on the button
- pageupText: Full text shown in action selection
- pagedownKey: Short text shown on the button
- pagedownText: Full text shown in action selection

## Installation

1. Download `PSYCHRONIC_GamepadConfigMZ.js`.
2. Place it in your RPG Maker MZ project's `js/plugins/` folder.
3. Enable it from the RPG Maker Plugin Manager.
4. Configure any plugin parameters or commands listed below.

## Full Plugin Help

### Introduction

This plugin allows players to customize their gamepad controls from the
Options menu. It features a visual gamepad diagram where players can click
on buttons to assign actions. Both Standard and Alternative layouts are
supported by default.

### Features

- Visual gamepad diagram for easy configuration
- Standard and Alternative gamepad layouts included
- Click on any button to assign an action
- Assign actions like OK, Cancel, Menu, Dash, etc.
- Controller outline for visual clarity
- Saves configuration automatically
- Full keyboard/mouse support for navigation
- Integrates with MegaOptions plugin

### Integration with MegaOptions

To add Gamepad Config to your MegaOptions menu, create an option with:

Name: Gamepad Config
Symbol: gamepadConfig
Default Value: false
Help Description: Customize your gamepad controls.

Process OK Code:
SceneManager.push(Scene_GamepadConfig);

Draw Item Code:
var rect = this.itemLineRect(index);
this.resetTextColor();
this.changePaintOpacity(this.isCommandEnabled(index));
this.drawText(this.commandName(index), rect.x, rect.y, rect.width, "left");

### Usage

1. Access from Options Menu
2. Click on a button you want to change
3. Select the action you want to assign to that button
4. Use "Default Layout" or "Alt Layout" to quick-switch
5. Press "Finish" when done

### Version History

v1.0.5 - Enhanced startup gamepad detection
- Fixed: Gamepads now properly activate when already connected at game start
- Added: Multiple detection mechanisms for maximum compatibility
1. Continuous frame-by-frame polling via Input.update()
2. Independent 100ms interval polling (10 seconds)
3. Keyboard/mouse/touch event listeners trigger instant gamepad check
- Added: Automatic detection when user presses ANY key or clicks mouse
- Added: Detection of gamepad state transitions (null to active)
- Enhanced: Comprehensive logging for debugging gamepad detection
- Browser security note: Gamepads require user interaction to activate
- Solution: Simply press any key, click mouse, or press controller button at start

v1.0.4 - Linux gamepad initialization fix
- Fixed: Gamepad now properly detected on Linux when plugged in before game starts
- Added: Input._initializeGamepadsAtStartup() to manually initialize gamepad state
- Added: Input._createGamepadState() helper for proper state creation
- Changed: Gamepad initialization triggered in Input.clear() and on timer at boot
- Linux-specific: No longer requires unplugging/replugging to detect gamepad

v1.0.3 - Global gamepad detection at startup
- Fixed: Gamepad now properly detected when connected before game starts
- Added: Global gamepad event listeners set up at plugin load
- Added: Forced gamepad polling during first 3 seconds of gameplay
- Added: Input._updateGamepads() method for manual gamepad refresh

v1.0.2 - Gamepad detection and highlight fixes
- Fixed: Yellow highlight no longer persists after button configuration
- Fixed: Gamepad now detected even when connected before game starts
- Added: Gamepad connection/disconnection event listeners
- Added: Continuous gamepad polling during scene (once per second)
- Cursor now moves to command buttons after assigning/clearing actions

v1.0.1 - Bug fixes and improvements
- Fixed: Window now properly activates on scene start
- Fixed: Keyboard/mouse navigation now works correctly
- Removed: Protected button restrictions (all buttons can be changed on PC)
- Controller outline drawn around buttons for visual clarity
- Keyboard/mouse support for navigation (Escape to exit)

v1.0.0 - Initial Release
- Visual gamepad configuration
- Standard and Alternative presets
- Full MZ compatibility
- Explicit clearRect to prevent graphics caching

@param ---General---
@default

@param commandName
@text Command Name
@parent ---General---
@desc The name shown in the Options menu
@default Gamepad Config

@param ---Help Text---
@default

@param buttonHelp
@text Button Help
@parent ---Help Text---
@desc Help text shown when hovering over a button
@default Select this button to change its assigned action.

@param defaultHelp
@text Default Layout Help
@parent ---Help Text---
@desc Help text for the Default Layout option
@default Reset to the default gamepad layout.

@param altHelp
@text Alt Layout Help
@parent ---Help Text---
@desc Help text for the Alternative Layout option
@default Change to alternative gamepad layout.

@param finishHelp
@text Finish Help
@parent ---Help Text---
@desc Help text for the Finish option
@default Save your gamepad configuration and return.

@param ---Colors---
@default

@param assignedColor
@text Assigned Button Color
@parent ---Colors---
@type number
@min 0
@max 31
@desc Background color for buttons with actions assigned
@default 21

@param selectedColor
@text Selected Button Color
@parent ---Colors---
@type number
@min 0
@max 31
@desc Background color for currently selected button
@default 17

@param protectedColor
@text Protected Button Color
@parent ---Colors---
@type number
@min 0
@max 31
@desc Background color for protected (locked) buttons
@default 2

@param actionColor
@text Action Text Color
@parent ---Colors---
@type number
@min 0
@max 31
@desc Text color for action names on buttons
@default 4

@param ---Action Names---
@default

@param clearText
@text Clear Action
@parent ---Action Names---
@desc Text for clearing a button assignment
@default Clear

@param okKey
@text OK Button Display
@parent ---Action Names---
@desc Short text shown on the button
@default OK

@param okText
@text OK Action Text
@parent ---Action Names---
@desc Full text shown in action selection
@default OK / Confirm / Talk

@param escapeKey
@text Cancel Button Display
@parent ---Action Names---
@desc Short text shown on the button
@default X

@param escapeText
@text Cancel Action Text
@parent ---Action Names---
@desc Full text shown in action selection
@default Cancel / Menu

@param menuKey
@text Menu Button Display
@parent ---Action Names---
@desc Short text shown on the button
@default Menu

@param menuText
@text Menu Action Text
@parent ---Action Names---
@desc Full text shown in action selection
@default Open Menu

@param shiftKey
@text Dash Button Display
@parent ---Action Names---
@desc Short text shown on the button
@default Dash

@param shiftText
@text Dash Action Text
@parent ---Action Names---
@desc Full text shown in action selection
@default Dash / Sprint

@param pageupKey
@text PageUp Button Display
@parent ---Action Names---
@desc Short text shown on the button
@default PgUp

@param pageupText
@text PageUp Action Text
@parent ---Action Names---
@desc Full text shown in action selection
@default Page Up / Prev Character

@param pagedownKey
@text PageDown Button Display
@parent ---Action Names---
@desc Short text shown on the button
@default PgDn

@param pagedownText
@text PageDown Action Text
@parent ---Action Names---
@desc Full text shown in action selection
@default Page Down / Next Character

## Source

This standalone repository is generated from the latest PSYCHRONIC plugin source in the RPG Reactor Complex template.

## License

MIT. See `LICENSE`.
