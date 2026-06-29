# Obsidian Cheat Sheet

> A comprehensive reference for shortcuts, markdown syntax, plugins, tips, and workflows.

---

## Table of Contents

1. [Keyboard Shortcuts](#keyboard-shortcuts)
2. [Markdown Syntax](#markdown-syntax)
3. [Plugins](#plugins)
4. [Tips & Concepts](#tips--concepts)
5. [Workflows](#workflows)

---

## Keyboard Shortcuts

> **Mac:** ⌘ = Command | **Windows/Linux:** Ctrl replaces ⌘, and Win replaces ⌥ where applicable

### Navigation

| Action | Mac | Windows / Linux |
|---|---|---|
| Quick switcher — open any file | ⌘ O | Ctrl O |
| Command palette | ⌘ P | Ctrl P |
| Navigate back | ⌘ Alt ← | Ctrl Alt ← |
| Navigate forward | ⌘ Alt → | Ctrl Alt → |
| Open graph view | ⌘ G | Ctrl G |
| Search in all files | ⌘ Shift F | Ctrl Shift F |
| Toggle left sidebar | ⌘ B | Ctrl B |
| Toggle right sidebar | ⌘ Shift B | Ctrl Shift B |

### Pane & Tab Management

| Action | Mac | Windows / Linux |
|---|---|---|
| New tab | ⌘ T | Ctrl T |
| Close current tab | ⌘ W | Ctrl W |
| Split pane vertically | ⌘ \ | Ctrl \ |
| Split pane horizontally | ⌘ - | Ctrl - |
| Go to next tab | ⌘ ` | Ctrl ` |
| Focus next pane | ⌘ Shift Tab | Ctrl Shift Tab |

### Editing

| Action | Mac | Windows / Linux |
|---|---|---|
| Create new note | ⌘ N | Ctrl N |
| Bold | ⌘ B | Ctrl B |
| Italic | ⌘ I | Ctrl I |
| Undo | ⌘ Z | Ctrl Z |
| Redo | ⌘ Shift Z | Ctrl Shift Z |
| Find / replace in note | ⌘ H | Ctrl H |
| Insert template | ⌘ Shift T | Ctrl Shift T |
| Insert internal link | ⌘ K | Ctrl K |
| Move line up / down | Alt ↑ / ↓ | Alt ↑ / ↓ |
| Duplicate line | ⌘ D | Ctrl D |
| Delete current line | ⌘ Shift K | Ctrl Shift K |

### View & Display

| Action | Mac | Windows / Linux |
|---|---|---|
| Toggle reading / edit mode | ⌘ E | Ctrl E |
| Toggle source / live preview | ⌘ Shift E | Ctrl Shift E |
| Zoom in | ⌘ + | Ctrl + |
| Zoom out | ⌘ - | Ctrl - |
| Toggle focus mode | ⌘ Shift F | Ctrl Shift F |

---

## Markdown Syntax

### Headings

```
# Heading 1
## Heading 2
### Heading 3
#### Heading 4
##### Heading 5
###### Heading 6
```

### Inline Formatting

| Syntax | Result |
|---|---|
| `**bold**` or `__bold__` | **bold** |
| `*italic*` or `_italic_` | *italic* |
| `~~strikethrough~~` | ~~strikethrough~~ |
| `==highlight==` | highlighted text |
| `` `inline code` `` | `inline code` |
| `H~2~O` | H₂O (subscript) |
| `E=mc^2^` | E=mc² (superscript) |

### Links & Embeds

| Syntax | Description |
|---|---|
| `[[Note name]]` | Link to a note |
| `[[Note\|Alias]]` | Link with custom display text |
| `[[Note#Heading]]` | Link to a specific section |
| `[[Note#^blockid]]` | Link to a specific block |
| `![[Note]]` | Embed an entire note |
| `![[image.png\|200]]` | Embed image at 200px width |
| `[text](https://url)` | External hyperlink |
| `#tagname` | Inline tag |

### Lists & Tasks

```markdown
- Bullet item
* Also a bullet item

1. Ordered item
2. Another item

- [ ] Unchecked task
- [x] Completed task
```

### Blocks & Callouts

**Fenced code block:**
```
```js
const x = 1;
```
```

**Blockquote:**
```markdown
> This is a quote
```

**Callout block:**
```markdown
> [!NOTE]
> This is a note callout.

> [!TIP]
> This is a tip.

> [!WARNING]
> This is a warning.

> [!DANGER]
> This is a danger callout.
```

Add `+` or `-` after the type to make callouts expanded/collapsed by default:
```markdown
> [!NOTE]+
> Expanded by default

> [!NOTE]-
> Collapsed by default
```

**Table:**
```markdown
| Column A | Column B |
|----------|----------|
| Cell 1   | Cell 2   |
| Cell 3   | Cell 4   |
```

**Horizontal rule:**
```markdown
---
```

### Frontmatter / Metadata

```yaml
---
title: My Note
tags: [ai, research]
date: 2024-01-01
status: draft
rating: 5
---
```

**Inline Dataview property:**
```
key:: value
```

### Math (LaTeX)

```
Inline: $E = mc^2$

Block:
$$
\int_a^b f(x)\,dx
$$
```

---

## Plugins

### Core Plugins (Built-in)

| Plugin | Description |
|---|---|
| **Graph view** | Visualizes all notes as an interactive network. Filterable by tags, folders, or search. |
| **Backlinks** | Shows every note that links to the current one. Surfaces related context automatically. |
| **Templates** | Insert reusable note templates with `{{date}}` and `{{title}}` variables. |
| **Daily notes** | Creates and opens a dated note for today. Great for journaling and task capture. |
| **Outline** | Live heading tree for the current note in the sidebar. Click to jump. |
| **Command palette** | Central hub for running any command. Assign custom hotkeys here. |
| **Canvas** | Infinite whiteboard for visual thinking — place notes, images, and cards freely. |
| **Sync** *(paid)* | Official end-to-end encrypted sync across all devices with version history. |

### Community Plugins

#### Top Picks

| Plugin | Description |
|---|---|
| **Dataview** | Query your vault like a database. Use DQL or inline JS to create dynamic tables and task views based on frontmatter and tags. |
| **Templater** | Powerful template engine with JavaScript, dynamic dates, file properties, and user scripts. Far more capable than core Templates. |
| **Calendar** | Adds a calendar widget to the sidebar. Click any date to create or open a daily note. Shows dot indicators for existing notes. |

#### Highly Rated

| Plugin | Description |
|---|---|
| **Periodic Notes** | Extends daily notes to weekly, monthly, quarterly, and yearly notes. Essential for time-based review systems. |
| **Tasks** | Adds due dates, recurrence, and priorities to checkboxes. Query tasks across the vault. |
| **Excalidraw** | Embed a full hand-drawn diagram tool in your notes. Drawings stored as text files so they sync with the vault. |

#### Power User

| Plugin | Description |
|---|---|
| **QuickAdd** | Capture ideas quickly to any file via hotkeys. Chain macros, run scripts, auto-move notes. |
| **Obsidian Git** | Auto-commits and pushes your vault to GitHub on a schedule. Free backup and version control. |

#### Quality of Life

| Plugin | Description |
|---|---|
| **Advanced Tables** | Tab-navigation and auto-formatting for markdown tables. Feels like editing a spreadsheet. |
| **Linter** | Auto-formats notes on save: spacing, YAML cleanup, heading capitalization. Keeps the vault tidy. |

#### Other Notable Plugins

| Plugin | Description |
|---|---|
| **Mind Map** | Converts any note's headings and bullets into an interactive mind map. |
| **Kindle Highlights** | Imports Kindle highlights directly into Obsidian as notes, organized by book. |

---

## Tips & Concepts

### Core Concepts

**Wikilinks are the backbone**
Use `[[Note Name]]` liberally. The power of Obsidian is in links — they create relationships even before you consciously plan them. Don't worry about being "correct"; link freely and let the graph reveal structure.

**Vault structure**
Avoid deep folder hierarchies. A flat structure with good tags and links outperforms nested folders. Consider PARA (Projects, Areas, Resources, Archive) or MOC (Maps of Content) approaches.

**Maps of Content (MOC)**
Create "hub" notes that link to all related notes on a topic. MOCs act as indices. A `[[Python MOC]]` links to every Python note. Better than folders for fluid, evolving organization.

**Tags vs. links**
- Use **tags** for properties and status: `#status/active`, `#type/book`
- Use **links** for conceptual relationships
- Tags are flat categorization; links build a semantic network. Both can coexist.

**Your vault is plain text**
All notes are `.md` files — no proprietary format, no lock-in. Edit in any text editor. Back up with Git, Dropbox, or any file sync. Your data is always yours.

**Frontmatter is searchable**
The YAML block at the top of a note lets you add structured metadata. Dataview can query it like a database — great for book ratings, project status, dates, and people.

**Nested tags**
Use `#project/work` and `#project/personal` to nest tags. The tag panel shows them hierarchically. Useful for status: `#status/draft`, `#status/done`.

**Unlinked mentions**
Obsidian surfaces mentions of a note's name even without a formal link. Check Backlinks → "Unlinked mentions" to discover and convert them to real links.

### Power Features

**Block references**
Add `^blockid` after any paragraph, then link with `[[Note#^blockid]]` or transclude with `![[Note#^blockid]]`. Reference exact sentences across notes.

**Collapsible callouts**
```markdown
> [!NOTE]+   ← expanded by default
> [!NOTE]-   ← collapsed by default
```

**Dataview query example**
````markdown
```dataview
TABLE status, tags FROM #project
WHERE status = "active"
SORT file.mtime DESC
```
````

**Inline Dataview**
```
`= this.status`       — shows current note's status field
`= [[Note]].rating`   — shows another note's rating field
```

---

## Workflows

### 1. Daily Notes System (Journaling + GTD)

Capture daily thoughts, tasks, and meeting notes in a dated note. Use a Templater template to auto-populate structure. Roll up unfinished tasks with Dataview. Review weekly.

**Setup steps:**
1. Enable Daily Notes core plugin + install Templater
2. Create a daily template with sections (Tasks, Notes, Log)
3. Use the Calendar plugin to navigate dates
4. Add a Dataview query to surface open tasks across all daily notes

**Example Dataview query for open tasks:**
````markdown
```dataview
TASK FROM "Daily Notes"
WHERE !completed
SORT file.mtime DESC
```
````

---

### 2. Book / Reading Notes (Zettelkasten)

One note per book with frontmatter metadata. Extract highlights as atomic notes, link them to idea notes. Let the graph reveal cross-book patterns.

**Setup steps:**
1. Create a book note template with YAML: `author`, `rating`, `status`, `date-read`
2. Extract key ideas as separate atomic notes
3. Link all book notes to a `[[Books MOC]]`
4. Use Kindle Highlights plugin for direct import

**Example Dataview table:**
````markdown
```dataview
TABLE author, rating, status FROM #book
SORT rating DESC
```
````

---

### 3. Project Management (PARA)

Organize with 4 top-level folders: **Projects** (active, outcome-based), **Areas** (ongoing responsibility), **Resources** (reference), **Archive** (completed).

**Setup steps:**
1. Create 4 top-level folders: `Projects/`, `Areas/`, `Resources/`, `Archive/`
2. One index note per project with goals, tasks, and links
3. Use the Tasks plugin for due dates and priorities
4. Dataview query for all open project tasks

**Example index note structure:**
```markdown
# Project: Website Redesign

## Goal
Launch by Q3 2025.

## Tasks
- [ ] Wireframes 📅 2025-02-01
- [ ] Copy review 📅 2025-02-15

## Notes
[[Design brief]] | [[Stakeholder meeting 2025-01-10]]
```

---

### 4. Personal CRM

One note per person with frontmatter. Log meetings chronologically. Dataview surfaces people you haven't talked to recently.

**Setup steps:**
1. Create a person note template with YAML: `company`, `met`, `last-contact`, tags
2. Tag all people notes with `#person`
3. Log meetings as dated sub-sections within the note
4. Dataview query sorted by last-contact date

**Example Dataview query:**
````markdown
```dataview
TABLE company, last-contact FROM #person
SORT last-contact ASC
```
````

---

### 5. Writing / Publishing Pipeline

Draft in Obsidian, track status in frontmatter, export when ready.

**Setup steps:**
1. Add `status:: draft` to frontmatter of every piece
2. Dataview view of all notes by status
3. Install Pandoc plugin for export to PDF or DOCX
4. Move published notes to `Archive/`

**Status progression:** `draft` → `editing` → `ready` → `published`

**Example Dataview pipeline view:**
````markdown
```dataview
TABLE status, file.mtime AS "Last edited" FROM "Writing"
SORT status ASC
```
````

---

### 6. Backup & Sync with Git

Free version control and backup using Git + GitHub.

**Setup steps:**
1. Run `git init` inside your vault folder
2. Create a private GitHub repository
3. Install the **Obsidian Git** community plugin
4. Set auto-commit interval (e.g. every 10 minutes) and enable auto-push

**Useful Obsidian Git commands (via Command Palette):**
- `Obsidian Git: Commit all changes`
- `Obsidian Git: Push`
- `Obsidian Git: Pull`
- `Obsidian Git: Open history`

---

*Generated with Claude — obsidian.md*
