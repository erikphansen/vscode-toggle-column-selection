# Toggle Column Selection for [Visual Studio Code](http://code.visualstudio.com)

> Adds a [TextMate 2](https://macromates.com)-style `Toggle Column Selection` command to VSCode

![Demo](images/demo.gif)

## Features ##

- Converts a single contiguous selection into a column selection composed of multiple selections/cursors.
- Also works in the opposite direction, converting multiple selections/cursors into a single contiguous selection.

## Usage

1. Make a multi-line selection, idealy using your keyboard by holding the `SHIFT` key while using the arrow keys to move the cursor.
2. Invoke the `Toggle Column Selection` command from the Command Palette (`COMMAND`-`SHIFT`-`P`) or the default keybinding (`OPTION`-`SHIFT`-`I`).

### Settings (Configuration)

You can configure how the line length affects the selection in that line by setting the following:

```
"toggleColumnSelection.inLineInSelectionRange": "none"
```

Possible values are:

```
"none"    - This is the default. A line in will always have a selection cursor.
"partial" - A line will have a selection cursor if it is longer enough to be 
            in the range of selection, albeit partially.
"full"    - A line will always have a selection cursor only if it is long
            enough to be fully in selection range.
```

### Crank It To Eleven (aka Tap `OPTION` to Invoke)

To truly mimic TextMate's implementation you'll want to trigger this command with a single tap of the `OPTION` key. Sadly VSCode won't allow you to do this. This is where [BetterTouchTool](https://www.boastr.net) comes in. Use BTT to set up a new Key Sequence that maps a single tap of the `OPTION` key to `OPTION`-`SHIFT`-`I`.

![BTT-1](images/btt-1.png)
![BTT-2](images/btt-2.png)

**BetterTouchTool TIPS:**

- Make sure you check the `REQUIRED` and `ORDER RELEVANT` boxes for the **KEY UP** state.
- BetterTouchTool treats the left and right `OPTION` keys as different keys so you'll likely want to create an entry for each key.
