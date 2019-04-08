# Toggle Column Selection for [Visual Studio Code](http://code.visualstudio.com)

> Adds a [TextMate 2](https://macromates.com)-style `Toggle Column Selection` command to VSCode

![Demo](images/demo.gif)

## Features

- Converts a single contiguous selection into a column selection composed of multiple selections/cursors.
- Also works in the opposite direction, converting multiple selections/cursors into a single contiguous selection.

## Usage

1. Make a multi-line selection, idealy using your keyboard by holding the `SHIFT` key while using the arrow keys to move the cursor.
2. Invoke the `Toggle Column Selection` command from the Command Palette  or use the default keybinding (`OPTION/ALT`-`SHIFT`-`I`).

> Note that this extension's default keybinding overrides the default keybinding for the built-in `Add Cursors to Line Ends` command. But chances are you don't like how that command works or you wouldn't be using the Toggle Column Selection extension.

## Crank It To Eleven (aka Tap `OPTION` to Invoke)

> This section only applies to macOS & Windows. If you know tools for Linux that let you trigger actions by simply tapping a modifier key, please let me know or submit a PR.

### macOS

To truly mimic TextMate's implementation you'll want to trigger this command with a single tap of the `OPTION` key. Sadly VSCode won't allow you to do this. This is where [Karabiner Elements](https://pqrs.org/osx/karabiner/) or [BetterTouchTool](https://www.boastr.net) come in.

#### Option A: Karabiner Elements

Add the following entry to the `rules` array in your `karabiner.json` file (located at `~/.config/karabiner/karabiner.json`):

```json
{
  "description": "Tap ⌥ to Toggle Column Selection in VSCode",
  "manipulators": [
    {
      "from": {
        "key_code": "left_option"
      },
      "to": [
        {
          "key_code": "left_option"
        }
      ],
      "to_if_alone": [
        {
          "key_code": "i",
          "modifiers": [
            "left_shift",
            "left_option"
          ]
        }
      ],
      "type": "basic",
      "conditions": [
        {
          "type": "frontmost_application_if",
          "bundle_identifiers": [
            "com.microsoft.VSCode"
          ]
        }
      ]
    },
    {
      "from": {
        "key_code": "right_option"
      },
      "to": [
        {
          "key_code": "right_option"
        }
      ],
      "to_if_alone": [
        {
          "key_code": "i",
          "modifiers": [
            "left_shift",
            "left_option"
          ]
        }
      ],
      "type": "basic",
      "conditions": [
        {
          "type": "frontmost_application_if",
          "bundle_identifiers": [
            "com.microsoft.VSCode"
          ]
        }
      ]
    }
  ]
}
```

Or use this handy URL to install the rule directly into Karabiner: `karabiner://karabiner/assets/complex_modifications/import?url=https://raw.githubusercontent.com/erikphansen/vscode-toggle-column-selection/master/karabiner/option-toggle-column-selection-vscode.json`. (It seems that GitHub will not allow that to be a clickable link.)

#### Option B: BetterTouchTool

If you don't want to use Karabiner, you can use BTT to set up a new Key Sequence that maps a single tap of the `OPTION` key to `OPTION`-`SHIFT`-`I`.

![BTT-1](images/btt-1.png)
![BTT-2](images/btt-2.png)

**BetterTouchTool TIPS:**

1. Make sure you check the `REQUIRED` and `ORDER RELEVANT` boxes for the **KEY UP** state.
2. BetterTouchTool treats the left and right `OPTION` keys as different keys so you'll likely want to create an entry for each key.

### Windows

#### AutoHotkey

If you don't have AutoHotkey installed yet, grab it at [https://www.autohotkey.com](https://www.autohotkey.com/). Then, in your `autohotkey.ahk` script:

```ahk
#IfWinActive Visual Studio Code
    ; on LALT key-up, send ALT+SHIFT+I
    LAlt Up::SendInput !+i
#IfWinActive
```
