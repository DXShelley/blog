---
title: chrome快捷键汇总
tags:
  - tools
  - chrome
  - shortcuts
categories:
  - tool
  - chrome
date: 2021-12-21 17:26:00
---

# # chrome快捷键汇总

## Keyboard shortcuts for opening DevTools

To open DevTools, press the following keyboard shortcuts while your cursor is focused on the browser viewport:

| Action                            | Mac                                 | Windows / Linux     |
| --------------------------------- | ----------------------------------- | ------------------- |
| Open whatever panel you used last | Command+Option+I                    | F12 or Ctrl+Shift+I |
| Open the **Console** panel        | Command+Option+J                    | Ctrl+Shift+J        |
| Open the **Elements** panel       | Command+Shift+C or Command+Option+C | Ctrl+Shift+C        |

## [#](https://developer.chrome.com/docs/devtools/shortcuts/#global)Global keyboard shortcuts

The following keyboard shortcuts are available in most, if not all, DevTools panels.

| Action                                                       | Mac                                                          | Windows / Linux                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Show **Settings**                                            | ? or Function+F1                                             | ? or F1                                                      |
| Focus the next panel                                         | Command+]                                                    | Ctrl+]                                                       |
| Focus the previous panel                                     | Command+[                                                    | Ctrl+[                                                       |
| Switch back to whatever [docking position](https://developer.chrome.com/docs/devtools/customize/#placement) you last used. If DevTools has been in its default position for the entire session, then this shortcut undocks DevTools into a separate window | Command+Shift+D                                              | Ctrl+Shift+D                                                 |
| Toggle **[Device Mode](https://developer.chrome.com/docs/devtools/device-mode/)** | Command+Shift+M                                              | Ctrl+Shift+M                                                 |
| Toggle **Inspect Element Mode**                              | Command+Shift+C                                              | Ctrl+Shift+C                                                 |
| Open the **[Command Menu](https://developer.chrome.com/docs/devtools/command-menu/)** | Command+Shift+P                                              | Ctrl+Shift+P                                                 |
| Toggle the **[Drawer](https://developer.chrome.com/docs/devtools/customize/#drawer)** | Escape                                                       | Escape                                                       |
| Normal reload                                                | Command+R                                                    | F5 or Ctrl+R                                                 |
| Hard reload                                                  | Command+Shift+R                                              | Ctrl+F5 or Ctrl+Shift+R                                      |
| Search for text within the current panel. Not supported in the **Audits**, **Application**, and **Security** panels | Command+F                                                    | Ctrl+F                                                       |
| Opens the **Search** tab in the **[Drawer](https://developer.chrome.com/docs/devtools/customize/#drawer)**, which lets you search for text across all loaded resources | Command+Option+F                                             | Ctrl+Shift+F                                                 |
| Open a file in the **Sources** panel                         | Command+O or Command+P                                       | Ctrl+O or Ctrl+P                                             |
| Zoom in                                                      | Command+Shift++                                              | Ctrl+Shift++                                                 |
| Zoom out                                                     | Command+-                                                    | Ctrl+-                                                       |
| Restore default zoom level                                   | Command+0                                                    | Ctrl+0                                                       |
| Run snippet                                                  | Press Command+O to open the **[Command Menu](https://developer.chrome.com/docs/devtools/command-menu/)**, type ! followed by the name of the script, then press Enter | Press Ctrl+O to open the **[Command Menu](https://developer.chrome.com/docs/devtools/command-menu/)**, type ! followed by the name of the script, then press Enter |

## [#](https://developer.chrome.com/docs/devtools/shortcuts/#elements)Elements panel keyboard shortcuts

| Action                                                       | Mac                                                          | Windows / Linux                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Undo change                                                  | Command+Z                                                    | Ctrl+Z                                                       |
| Redo change                                                  | Command+Shift+Z                                              | Ctrl+Y                                                       |
| Select the element above / below the currently-selected element | Up Arrow / Down Arrow                                        | Up Arrow / Down Arrow                                        |
| Expand the currently-selected node. If the node is already expanded, this shortcut selects the element below it | Right Arrow                                                  | Right Arrow                                                  |
| Collapse the currently-selected node. If the node is already collapsed, this shortcut selects the element above it | Left Arrow                                                   | Left Arrow                                                   |
| Expand or collapse the currently-selected node and all of its children | Hold Option then click the arrow icon next to the element's name | Hold Ctrl+Alt then click the arrow icon next to the element's name |
| Toggle **Edit Attributes** mode on the currently-selected element | Enter                                                        | Enter                                                        |
| Select the next / previous attribute after entering **Edit Attributes** mode | Tab / Shift+Tab                                              | Tab / Shift+Tab                                              |
| Hide the currently-selected element                          | H                                                            | H                                                            |
| Toggle **Edit as HTML** mode on the currently-selected element | Function+F2                                                  | F2                                                           |

### [#](https://developer.chrome.com/docs/devtools/shortcuts/#styles)Styles pane keyboard shortcuts

| Action                                                       | Mac                                                          | Windows / Linux                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Go to the line where a property value is declared            | Hold Command then click the property value                   | Hold Ctrl then click the property value                      |
| Cycle through the RBGA, HSLA, and Hex representations of a color value | Hold Shift then click the **Color Preview** box next to the value | Hold Shift then click the **Color Preview** box next to the value |
| Select the next / previous property or value                 | Click a property name or value then press Tab / Shift+Tab    | Click a property name or value then press Tab / Shift+Tab    |
| Increment / decrement a property value by 0.1                | Click a value then press Option+Up Arrow / Option+Down Arrow | Click a value then press Alt+Up Arrow / Alt+Down Arrow       |
| Increment / decrement a property value by 1                  | Click a value then press Up Arrow / Down Arrow               | Click a value then press Up Arrow / Down Arrow               |
| Increment / decrement a property value by 10                 | Click a value then press Shift+Up Arrow / Shift+Down Arrow   | Click a value then press Shift+Up Arrow / Shift+Down Arrow   |
| Increment / decrement a property value by 100                | Click a value then press Command+Up Arrow / Command+Down Arrow | Click a value then press Ctrl+Up Arrow / Ctrl+Down Arrow     |
| Cycle through the degrees (deg), gradians (grad), radians (rad) and turns (turn) representations of an angle value | Hold Shift then click the **Angle Preview** box next to the value | Hold Shift then click the **Angle Preview** box next to the value |
| Increment / decrement an angle value by 1                    | Click the **Angle Preview** box next to the value then press Up Arrow / Down Arrow | Click the **Angle Preview** box next to the value then press Up Arrow / Down Arrow |
| Increment / decrement an angle value by 10                   | Click the **Angle Preview** box next to the value then press Shift+Up Arrow / Shift+Down Arrow | Click the **Angle Preview** box next to the value then press Shift+Up Arrow / Shift+Down Arrow |
| Increment / decrement an angle value by 15                   | Click the **Angle Preview** box next to the value then press Shift, click / mouse slide on the **Angle Clock Overlay** | Click the **Angle Preview** box next to the value then press Shift, click / mouse slide on the **Angle Clock Overlay** |

## [#](https://developer.chrome.com/docs/devtools/shortcuts/#sources)Sources panel keyboard shortcuts

| Action                                                       | Mac                                                          | Windows / Linux                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Pause script execution (if currently running) or resume (if currently paused) | F8 or Command+\                                              | F8 or Ctrl+\                                                 |
| Step over next function call                                 | F10 or Command+'                                             | F10 or Ctrl+'                                                |
| Step into next function call                                 | F11 or Command+;                                             | F11 or Ctrl+;                                                |
| Step out of current function                                 | Shift+F11 or Command+Shift+;                                 | Shift+F11 or Ctrl+Shift+;                                    |
| [Continue to a certain line of code while paused](https://developer.chrome.com/blog/new-in-devtools-60/#continue) | Hold Command and then click the line of code                 | Hold Ctrl and then click the line of code                    |
| Select the call frame below / above the currently-selected frame | Ctrl+. / Ctrl+,                                              | Ctrl+. / Ctrl+,                                              |
| Save changes to local modifications                          | Command+S                                                    | Ctrl+S                                                       |
| Save all changes                                             | Command+Option+S                                             | Ctrl+Alt+S                                                   |
| Go to line                                                   | Ctrl+G                                                       | Ctrl+G                                                       |
| Jump to a line number of the currently-open file             | Press Command+O to open the **[Command Menu](https://developer.chrome.com/docs/devtools/command-menu/)**, type : followed by the line number, then press Enter | Press Ctrl+O to open the **[Command Menu](https://developer.chrome.com/docs/devtools/command-menu/)**, type : followed the line number, then press Enter |
| Jump to a column of the currently-open file (for example line 5, column 9) | Press Command+O to open the **[Command Menu](https://developer.chrome.com/docs/devtools/command-menu/)**, type :, then the line number, then another :, then the column number, then press Enter | Press Ctrl+O to open the **[Command Menu](https://developer.chrome.com/docs/devtools/command-menu/)**, type :, then the line number, then another :, then the column number, then press Enter |
| Go to a function declaration (if currently-open file is HTML or a script), or a rule set (if currently-open file is a stylesheet) | Press Command+Shift+O, then type in the name of the declaration / rule set, or select it from the list of options | Press Ctrl+Shift+O, then type in the name of the declaration / rule set, or select it from the list of options |
| Close the active tab                                         | Option+W                                                     | Alt+W                                                        |

### [#](https://developer.chrome.com/docs/devtools/shortcuts/#editor)Code Editor keyboard shortcuts

| Action                                                       | Mac                                                    | Windows / Linux                                     |
| ------------------------------------------------------------ | ------------------------------------------------------ | --------------------------------------------------- |
| Delete all characters in the last word, up to the cursor     | Option+Delete                                          | Ctrl+Delete                                         |
| Add or remove a [line-of-code breakpoint](https://developer.chrome.com/docs/devtools/javascript/breakpoints#loc) | Focus your cursor on the line and then press Command+B | Focus your cursor on the line and then press Ctrl+B |
| Go to matching bracket                                       | Ctrl+M                                                 | Ctrl+M                                              |
| Toggle single-line comment. If multiple lines are selected, DevTools adds a comment to the start of each line | Command+/                                              | Ctrl+/                                              |
| Select / de-select the next occurrence of whatever word the cursor is on. Each occurrence is highlighted simultaneously | Command+D / Command+U                                  | Ctrl+D / Ctrl+U                                     |

## [#](https://developer.chrome.com/docs/devtools/shortcuts/#performance)Performance panel keyboard shortcuts

| Action                 | Mac       | Windows / Linux |
| ---------------------- | --------- | --------------- |
| Start / stop recording | Command+E | Ctrl+E          |
| Save recording         | Command+S | Ctrl+S          |
| Load recording         | Command+O | Ctrl+O          |

## [#](https://developer.chrome.com/docs/devtools/shortcuts/#memory)Memory panel keyboard shortcuts

| Action                 | Mac       | Windows / Linux |
| ---------------------- | --------- | --------------- |
| Start / stop recording | Command+E | Ctrl+E          |

## [#](https://developer.chrome.com/docs/devtools/shortcuts/#console)Console panel keyboard shortcuts

| Action                                                       | Mac                                                          | Windows / Linux                |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------ |
| Accept autocomplete suggestion                               | Right Arrow or Tab                                           | Right Arrow or Tab             |
| Reject autocomplete suggestion                               | Escape                                                       | Escape                         |
| Get previous statement                                       | Up Arrow                                                     | Up Arrow                       |
| Get next statement                                           | Down Arrow                                                   | Down Arrow                     |
| Focus the **Console**                                        | Ctrl+`                                                    | Ctrl+` |                                |
| Clear the **Console**                                        | Command+K or Option+L                                        | Ctrl+L                         |
| Force a multi-line entry. Note that DevTools should detect multi-line scenarios by default, so this shortcut is now usually unnecessary | Command+Return                                               | Shift+Enter                    |
| Execute                                                      | Return                                                       | Enter                          |
| Expand all sub-properties of an object that's been logged to the Console | Hold Alt then click **Expand**![img](https://developer.chrome.com/docs/devtools/images/expand.png) | Hold Alt then click **Expand** |

