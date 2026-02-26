# Bookmark Triage

A fast, keyboard-driven app for sorting through 1,327 bookmarks. Built with Dragon Design System styling.

## Quick Deploy

```bash
# Unpack
mkdir bookmark-triage && cd bookmark-triage
tar xzf ~/Downloads/bookmark-triage.tar.gz

# Push to GitHub
gh repo create bookmark-triage --public --source=. --push

# Deploy to Vercel
vercel
```

Vercel will auto-deploy on every push after the first `vercel` command.

## Or Run Locally

Just open `public/index.html` in your browser. Everything works offline.

## How to Use

### Triage Workflow
1. Click a bookmark (or press ↓) to select it — preview loads on the right
2. Decide: **Keep**, **★ Priority**, or **Delete**
3. App auto-advances to the next undecided bookmark
4. When done, hit **Export Bookmarks** to get a clean HTML file
5. Import that file into Chrome (Bookmark Manager → ⋮ → Import bookmarks)

### Keyboard Shortcuts
| Key | Action |
|-----|--------|
| `K` | Keep |
| `S` | ★ Star / Priority |
| `D` | Delete |
| `↑` `↓` | Navigate bookmarks |
| `Z` | Undo last action |
| `/` | Focus search box |
| `Esc` | Exit search |

### Bulk Actions
Each folder group has **All Keep** and **All Delete** buttons to handle entire folders at once.

### Filters
Toggle between All, Undecided, Keep, ★ Priority, and Delete views using the filter pills.

### Search
Type in the search box to filter by title, URL, or original folder name.

## Saving Progress

- **Auto-save**: Decisions save to your browser's localStorage automatically
- **Save JSON**: Export a portable JSON backup of all decisions (can't be re-imported yet, but preserves your work)
- **Reset All**: Clears all decisions and starts over

## Export

- **Export Bookmarks**: Generates a standard Netscape bookmark HTML file with only your Keep + Priority bookmarks. Priority items get their own ★ folder at the top.
- **Save JSON**: Exports all bookmarks with their decisions as JSON.

## Project Structure

```
bookmark-triage/
├── public/
│   ├── index.html        # The app (single file, no build step)
│   └── bookmarks.json    # Your 1,327 deduplicated bookmarks
├── vercel.json           # Vercel routing config
├── package.json          # Project metadata
└── README.md
```

## Notes

- Some sites block iframe previews (Google, SharePoint, etc.) — use "Open in new tab ↗" for those
- localStorage is per-domain, so your Vercel URL and localhost will have separate saved progress
- The bookmark data is baked into `bookmarks.json` — to update, re-export from Chrome and replace the file
