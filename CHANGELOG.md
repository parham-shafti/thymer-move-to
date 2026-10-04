# Changelog

## v1.3.1 - 2026-10-04

- **New note in a collection** now takes two clear steps: first find and pick the collection (typing filters the list), then name the page. The title starts out as the first line you're moving; keep it and that line becomes the title instead of also staying in the body (only for a plain-text line without children). The old single field asked for a title while it looked like a collection search.
- Fixed: **Nest under target** on a heading indents the moved content again. Since Thymer 1.0.20 a heading's content sits flush with the heading, so moved lines landed directly under it with no indent. They are now indented under the heading the way `Tab` does it, placed right below the heading.
- Fixed: a page's headings are listed in their real order, indented by how they nest, and labelled with their real level (`H1`, `H2`, `H3`). Nested headings used to end up at the bottom of the list, and every row said H1.
- Fixed: the collection lists (moving pages, and *New note in a collection…*) now include every collection, also ones hidden from the sidebar, each with its own icon. The new-note list is sorted by name, and the page-move search no longer stops at 14 collections.
- Search shows more results (up to 40 pages and 20 lines).
- Fixed: moving a line off a future Journal day (tomorrow or later) no longer fails with "Source page not found".
- Fixed: a rare case where sending to the Journal could create a misnamed Journal page.

## v1.3.0 — 2026-07-19

- **Move whole pages between collections.** Open a collection as a table, board, or gallery, run **Move pages…** (or the shortcut), select rows/cards (shift-click for a range), and send them to another collection. Running it on a single open page moves just that page. Properties missing in the destination are hidden but kept.
- **New note as a destination** for moving content: choose *New note in a collection…*, type a title, pick a collection, and the moved line/block/selection becomes the new note's body. Contributed by [@phildrysdale1](https://github.com/phildrysdale1) (#1).
- In page-selection mode the shortcut now advances: press once to select, again (with a selection) to open the collection picker, or with nothing selected to exit. `Escape` and the **Cancel** button also exit.
- New plugin icon, and every in-app icon swapped to ones Thymer's icon set actually renders (some were showing blank).

## v1.2.0 — 2026-07-11

- The destination picker now looks and searches like Thymer's native command palette: the same surface, mono font, corner radius, selected-row accent, and crisp match highlight.
- Every result shows the record's own icon (or its collection's icon) instead of a generic glyph, so pages and lines are easier to tell apart at a glance.
- Better search: page titles are scanned across the whole workspace and ranked by match quality (exact > starts-with > word boundary > contains), with more results shown (pages 12, lines 10).
- Hovering a line result now shows a floating preview of its full text (a line can be a whole paragraph the row truncates), with the matched words highlighted.
- Type a date (e.g. `tomorrow`, `next friday`, `2026-07-20`, `yesterday`) to move the content into that day's Journal, not just today's.

## v1.1.0 — 2026-07-03

- New **Top of page** placement: picking a destination page with content now offers *Top of page*, *Bottom of page* (still the default on Enter), and its headings. Empty pages skip the extra step.
- Fixed: moving several lines to an *empty* destination (an empty page, an empty heading section) placed them in reverse order. Single-line moves and destinations with content were unaffected.

## v1.0.1 — 2026-07-02

- Fixed page search: results are now ranked by how well the title matches (exact > starts-with > word boundary > contains), so a page named exactly what you typed comes first.
- Just-created pages are found immediately (pages are now also scanned directly by name; the workspace search index lags behind).
- Page results raised from 6 to 8.

## v1.0.0 — 2026-07-02

- Move the caret line, a whole block (parent + children), or a multi-line selection to another destination with a floating picker anchored at the selection.
- Destinations: today's Journal (default), any page (bottom or under a chosen heading), or any individual line — found with a fast search where `+` requires every word to match.
- Indent toggle: nest the moved content under the chosen heading/line, or place it directly after as a sibling. The choice persists.
- Scope toggle when the caret line has children: move the whole block, or only the line itself (its children stay, promoted one level).
- Content is moved, not copied as text — references, dates, tags and the whole subtree structure survive intact.
- Configurable shortcut (default `Cmd+Shift+M` / `Ctrl+Shift+M`) via the "Move To: Set Shortcut" command.
- Toast with an **Open** button that jumps to the moved content.
- Guards: refuses to move a block into itself, and refuses selections spanning multiple pages.
