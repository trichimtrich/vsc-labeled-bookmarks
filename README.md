# vsc-labeled-bookmarks README

Bookmarks with customizable icons, mouse free operation, able to jump to named bookmark directly. Bookmarks are organized into groups where you work with the active group, but can switch to another group any time.

**Important note on using breakpoints:**  Line decorations seem to interfere with placing breakpoints for debugging. To work around this, you can toggle the decorations on and off using `ctrl+alt+b h`. All operations still work the same when the decorations are hidden.

## Features

### Bookmarks

* You can set an unnamed bookmark on a line using `ctrl+alt+m`. If there already is a bookmark on the line, it is removed.
* Labeled bookmarks can be set using `ctrl+alt+l`. A prompt appears where you can type the label for the bookmark. **Labels are unique inside a group, so if you define the same label twice, the first bookmark that beared the label is deleted and only the new one remains.**
* The labeled bookmark creation is multifunctional: it expects the input in the format of "bookmark label" or "bookmark label@group name" or just "@group name. When a group name is specified, the group is created if it does not yet exist and it is set to be the active group. Then, if the label is specified, a new bookmark is created using it.
* Delete bookmarks using `ctrl+alt+b d`, or by using the above toggle commands on a line that already has a bookmark (of the active group).

### Navigation

* Go to the next bookmark: `ctrl+alt+k`
* Go to the previous bookmark: `ctrl+alt+j`
* Navigate to a bookmark by selecting it from a list: `ctrl+alt+n` A quick pick list appears where the bookmarks are filtered as you type. All bookmarks are displayed in the list, including the unamed ones.
* Navigate to a bookmark of any group (same as `ctrl+alt+n` but not limited to the active group): `ctrl+alt+b n`

### Groups

Most operations work on the currently active group's bookmarks. Each group has its own icon shape/color, but the inactive group icons appear semi transparent (or are hidden when `ctrl+alt+b i` is toggled).

Groups were implemented to be able to separate one set of bookmarks (for one topic/bug/branch etc.) from others. You can work with the set that is currently relevant, without other bookmarks littering the forward/backward navigation and and without having to delete them to avoid this.

* You can create a group and switch to it implicitly by using the "@" symbol when creating a labeled bookmark with `ctrl+alt+l`. See the relevant section above for details.
* Alternatively, you can create a group using `ctrl+alt+b alt+g`
* Delete one or multiple groups using `ctrl+alt+b shift+g`
* Select the active group from a list of the available groups: `ctrl+alt+b g`

### Display Options

* Hide / unhide bookmark icons (might be necessary to set a breakpoint on a line that also has a bookmark): `ctrl+alt+b h`
* Hide / unhide the icons of inactive groups: `ctrl+alt+b i`

### Customizing Group Icons

Group icons come in two variants: vector icons (fixed set) and unicode character icons (customizable set).

* Vector icons provide a fixed set of shapes to chose from, and they should appear the same accross all devices. When a new group is created it uses the sape specified as the default shape in the configuration options. If your group has a single character name, and it matches `[a-zA-Z0-9!?+-=\/\$%#]`, then the uppercased character is displayed on the icon.
* Unicode character icons can be customized using the `labeledBookmarks.unicodeMarkers` configuration option. You can define which unicode cahracters/symbol/emojis you would like to use as the group icon. These can be applied using the shape selection command `ctrl+alt+b s`. If none is defined, a default set is used. (Emojis have their own color and so the color setting remains ineffective on those, but it works as expected on the rest of the unicode alphabets and symbols.)

The other display option for group icons is the color.

* The icon color can be chosen selected from a list using `ctrl+alt+b c`. You can define the elements of this list with the configuration option `labeledBookmarks.colors`. If it is not defined a default color set is used.

## Extension Settings

* `labeledBookmarks.unicodeMarkers`: list of unicode characters to be made available in the shape selection list. It should be in the form of: `[["astonishing", "😲"], ["bug","🐞"]]`
* `labeledBookmarks.colors`: list of colors to be made available when creating new bookmark groups or when setting the color of an existing one. It should be in the form of: `[["red", "ff0000"], ["green", "00ff00"]]`
* `labeledBookmarks.defaultShape`: set which vector icon should be used as the default for new groups

## Known Issues

* Bookmark icons might interfere with placing breakponts. Use `ctrl+alt+b h` to hide/unhide the bookmark icons to avoid this.
* On Mac the backward navigation shortcut `ctrl+alt+j` is also used by the notebook editor command "join with next cell" with the activation condition "notebookEditorFocused". If you happen to be using that, you might want to change the assignment of either of these actions.
