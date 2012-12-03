# Emmet for Sublime Text 2 plugin

A work-in-progress official plugin for Sublime Text 2 with upcoming Emmet toolkit, previously called _Zen Coding_. This plugin will eventually replace the [current one](https://github.com/sublimator/ZenCoding).

*Warning:* this plugin may not work at all in some OSes since it written in JavaScript and uses [PyV8](http://code.google.com/p/pyv8/) and [Google V8](https://developers.google.com/v8/) binaries to run. If you experience problems or editor crashes please [fill an issue](https://github.com/sergeche/emmet-sublime/issues).

## How to install

-------------

**You should remove or disable previous Zen Coding plugin, installed from Package Control, in order to operate properly.**

-------------

1. Clone git repo into your packages folder (in ST2, find Browse Packages... menu item to open this folder)
2. Restart ST2 editor (if required)

Or with package control:

1. Package Control: Add Repository `https://github.com/sergeche/emmet-sublime`
2. Package Control: Install Package `emmet-sublime`
3. Restart ST2 editor (if required)

## New features of Emmet (compared with old Zen Coding)

* [Dynamic CSS abbreviations](http://docs.emmet.io/css-abbreviations/), automatic [vendor prefixes](http://docs.emmet.io/css-abbreviations/vendor-prefixes/) and [gradient generator](http://docs.emmet.io/css-abbreviations/gradients/).
* [“Lorem Ipsum” generator](http://docs.emmet.io/abbreviations/lorem-ipsum/)
* [Implicit tag names](http://docs.emmet.io/abbreviations/implicit-names/)
* New [Yandex’s BEM filter](http://docs.emmet.io/filters/bem/)
* [Extensions support](http://docs.emmet.io/customization/)
* New [^ operator](http://docs.emmet.io/abbreviations/syntax/)
* Various fixes and improvements

## Available actions ##

* [Expand Abbreviation](http://docs.emmet.io/actions/expand-abbreviation/) – <kbd>Tab</kbd> or <kbd>Ctrl+E</kbd>
* Interactive “Expand Abbreviation” — <kbd>Ctrl+Alt+Enter</kbd>
* [Match Tag Pair](http://docs.emmet.io/actions/match-pair/) – <kbd>⌃D</kbd> (Mac) / <kbd>Ctrl+,</kbd> (PC)
* [Wrap With Abbreviation](http://docs.emmet.io/actions/wrap-with-abbreviation/) — <kbd>⌃W</kbd> / <kbd>Shift+Ctrl+G</kbd>
* [Go to Edit Point](http://docs.emmet.io/actions/go-to-edit-point/) — <kbd>Ctrl+Alt+→</kbd> or <kbd>Ctrl+Alt+←</kbd>
* [Select Item](http://docs.emmet.io/actions/select-item/) – <kbd>⇧⌘.</kbd> or <kbd>⇧⌘,</kbd> / <kbd>Shift+Ctrl+.</kbd> or <kbd>Shift+Ctrl+,</kbd>
* [Toggle Comment](http://docs.emmet.io/actions/toggle-comment/) — <kbd>⌘/</kbd> / <kbd>Ctrl+/</kbd>
* [Split/Join Tag](http://docs.emmet.io/actions/split-join-tag/) — <kbd>⇧⌘'</kbd> / <kbd>Shift+Ctrl+`</kbd>
* [Remove Tag](http://docs.emmet.io/actions/remove-tag/) – <kbd>⌘'</kbd> / <kbd>Shift+Ctrl+;</kbd>
* [Update Image Size](http://docs.emmet.io/actions/update-image-size/) — <kbd>⇧⌃I</kbd> / <kbd>Ctrl+U</kbd>
* [Evaluate Math Expression](http://docs.emmet.io/actions/evaluate-math/) — <kbd>⇧⌘Y</kbd> / <kbd>Shift+Ctrl+Y</kbd>
* [Reflect CSS Value](http://docs.emmet.io/actions/reflect-css-value/) – <kbd>⇧⌘R</kbd> / <kbd>Shift+Ctrl+R</kbd>
* [Encode/Decode Image to data:URL](http://docs.emmet.io/actions/base64/) – <kbd>⇧⌃D</kbd> / <kbd>Ctrl+'</kbd>

[Increment/Decrement Number](http://docs.emmet.io/actions/inc-dec-number/) actions:

* Increment by 1: <kbd>Ctrl+↑</kbd>
* Decrement by 1: <kbd>Ctrl+↓</kbd>
* Increment by 0.1: <kbd>Alt+↑</kbd>
* Decrement by 0.1: <kbd>Alt+↓</kbd>
* Increment by 10: <kbd>⌥⌘↑</kbd> / <kbd>Shift+Alt+↑</kbd>
* Decrement by 10: <kbd>⌥⌘↓</kbd> / <kbd>Shift+Alt+↓</kbd>

## Extensions support ##

You can easily [extend](http://docs.emmet.io/customization/) Emmet with new actions and filters or customize existing ones. In `Emmet.sublime-settings`, define `extensions_path` setting and Emmet will load all `.js` and `.json` files in specified folder at startup.

## Overriding keyboard shortcuts ##

Sublime Text 2 is a great text editor with lots of features and actions. Most of these actions are bound to keyboard shortcuts so it’s nearly impossible to provide convenient plugin shortcuts for third-party plugins.

If you’re unhappy with default keymap, you can disable individual keyboard shortcuts with `disabled_keymap_actions` preference of `Emmet.sublime-settings` file.

Use a comma-separated list of action names which default keyboard shortcuts should be disabled. For example, if you want to release <kbd>Ctrl+E</kbd> (“Expand Abbreviation”) and <kbd>Ctrl+U</kbd> (“Update Image Size”) shortcuts, your must set the following value:

    "disabled_keymap_actions": "expand_abbreviation, update_image_size"

You should refer `Default (Your-OS-Name).sublime-keymap` file to get action ids (look for `args/action` key).

To disable all default shortcuts, set value to `all`:
    
    "disabled_keymap_actions": "all"

Not that if you disabled any action like so and you’re create your own keyboard shortcut, you **should not** use `emmet_action_enabled.ACTION_NAME` context since this is the key that disables action.

### “Help! My snippets doesn’t work anymore in HTML/CSS files!”

By default, Emmet overrides Tab key behaviour and expands its own abbreviations instead native snippets. You can either disable this feature in user preferences (add `"disable_tab_abbreviations": true` setting into your _Settings — User_ file) and use `Ctrl+E` or `Ctrl+Alt+Enter` to expand Emmet abbeviations or move your snippets to Emmet as described [here](https://github.com/sergeche/emmet-sublime/issues/16#issuecomment-8427268). I’m investigating possibility to expand native snippets via Emmet Tab key handler.
