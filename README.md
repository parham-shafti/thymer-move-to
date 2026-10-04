# Move To

Move To is a [Thymer](https://thymer.com) plugin for moving things without cut & paste. Two jobs:

1. **Move content** (a line, a whole block, or a multi-line selection) to another page, a heading, a specific line, a new note, or the Journal.
2. **Move whole pages** between collections, selecting them right in a table, board, or gallery view.

Press the shortcut (default `Cmd+Shift+M` / `Ctrl+Shift+M`) or run a command, and a small picker opens where you're working. Search the destination, hit Enter, done. Content is *moved*, not re-typed: references, dates, tags and the whole subtree survive intact, because it's the same operation as dragging things around in the editor.

![Moving a block and a multi-line selection to another page with the Move To picker](assets/move-to-demo.gif)

## Move content

Put the caret on a line (or select several) and open the picker. What moves is chosen automatically:

- a **multi-line selection** moves every selected line (blocks keep their children)
- a caret on a **parent line** moves the whole block by default; a toggle in the picker header switches to *Line only*, which leaves the children behind (promoted one level)
- a caret on a plain line moves just that line

**Destinations:**

- **Today's Journal** (default, just hit Enter), or type a date (`tomorrow`, `next friday`, `2026-07-20`) to move it into that day's Journal
- **a new note in any collection**: pick the collection, then name the page (the title starts out as the first line you move)
- **any page**, at the top, at the bottom, or under a heading you pick
- **any individual line**, anywhere in the workspace

**Fast search**, styled like Thymer's own command palette: each result carries its collection's icon, matched words are highlighted, `+` requires several words (`project+monday` matches lines with both), and hovering a line previews its full text.

**Indent toggle** (bottom left): nest the moved content *under* the chosen heading/line, or place it directly *after* it as a sibling. Your choice is remembered.

## Move pages between collections

Open a collection as a **table, board, or gallery** and run **Move pages…** (or press the shortcut). The view enters selection mode:

- click rows/cards to select them (clicking selects instead of opening), shift-click for a range
- press the shortcut again (or Enter, or the **Move to…** button) to open the collection picker
- search for the destination collection and confirm

Every selected page moves to that collection. Properties that don't exist in the destination are hidden but kept (they reappear if you move the page back). Journals and the current collection are left out of the list.

Running the command on a single open page moves just that page, no selection step.

Leave selection mode with **Escape**, the shortcut (when nothing is selected), or the **Cancel** button.

## Keyboard

- Type to search, `↑↓` to navigate, `↵` to move.
- A toast with an **Open** button jumps to where things landed.
- In page-selection mode: first shortcut press selects, second (with a selection) opens the picker, and with nothing selected it exits. `Escape` always exits.

## Installation

1. In Thymer, open the Command Palette (`Cmd+P` / `Ctrl+P`), run **Plugins**, and click **Create Plugin** under Global Plugins.
2. In the plugin's dialog, go to the code editor (click **Edit as Code** if you see the settings view).
3. In the **Custom Code** tab, replace the contents with [`plugin.js`](plugin.js).
4. In the **Configuration** tab, replace the contents with [`plugin.json`](plugin.json).
5. Click **Save**.

Don't enable Hot Reload — it's a development feature and can leave the plugin in a state where saved data stops persisting.

## Settings

- **Move To: Set Shortcut** (Command Palette) records a new shortcut. Include at least one of `Cmd` / `Ctrl` / `Alt`. Stored locally per device.
- The indent toggle state persists across sessions.

## Notes & limitations

- Moving content: a selection that spans multiple pages (e.g. across days in the Journal) is refused — select within one page.
- Inside the editor, Thymer captures `Escape` before plugins see it, so the content picker closes with click-outside, the `×`, or the shortcut. In a collection view (page mode), `Escape` works normally.
- The plugin is event-driven: nothing runs at idle except one keydown check for the shortcut.

## Credits

The "new note in a collection" destination was contributed by [@phildrysdale1](https://github.com/phildrysdale1).

## License

MIT
