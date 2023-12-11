OAKS (Obsidian Action and Knowledge System) is my proposal for an Obsidian powered second brain, naturally developed with OAKS itself!

# Installation

1. Clone or download and unzip this repo
2. Set it up as new Obsidian vault
3. Install Minimal theme
4. Install required plugins
    1. Advanced New File
    2. AidenLx's Folder Note
    3. Auto Link Title
    4. Codeblock Template
    5. Dataview
    6. Folder Note Core
    7. Icon Shortcodes
    8. Inline Scripts
    9. List Modified
    10. Natural Language Dates
    11. Supercharged Links
5. Install optional plugins
    1. Git
    2. Remotely Secure
6. Set optional git repository options
   ```bash
    git config core.autocrlf false # Obsidian works with LF only for now
    git config user.name <your name>
    git config user.email <your mail>
    git update-index --assume-unchanged .obsidian/plugins/obsidian-list-modified/data.json # Tracked notes are stored in plugin settings for now
    ```

# Roadmap

## Features

- [/] Quick capture (project, task, asset, date, link) [🏅:: 1]
- [ ] Quick edit [🏅:: 1]
- [/] Advanced view (reusable, drill down-able, sortable, filterable) [🏅:: 1]
- [ ] Auto journaling [🏅:: 3]
- [ ] Custom templates (item, collection, issue link) [🏅:: 3]
- [ ] Better file management (folder note, attachement) [🏅:: 3]
- [ ] Extended search (PDF, backlink)[🏅:: 3]
- [ ] Inbox and unresolved links processing [🏅:: 3]
- [ ] Extended import and export (CSV, slide deck, Word) [🏅:: 3]
- [ ] Self-hosted sync [🏅:: 3]

## UX

- [x] Non-clickable unresolved links [🏅:: 1] ✅ 2023-12-11
- [x] Sortable statuses (project, task) [🏅:: 1] ✅ 2023-12-11
- [x] Colored statuses [🏅:: 2] ✅ 2023-12-11
- [ ] Consistent task annotations [🏅:: 3]
- [ ] Custom task statuses transitions [🏅:: 3]
- [ ] Accent colored theme [🏅:: 3]
- [ ] Private and shared marker [🏅:: 3]
- [ ] Consistent desktop and mobile UX [🏅:: 3]

# Doc

- [ ] Install (desktop and mobile)
- [ ] Design rationales and inspirations
    - [ ] Name symbolism
    - [ ] Template plugin choice (autocomplete)
    - [ ] Note types
    - [ ] Sortable statuses (with UFT-8 special characters and icons)
    - [ ] Folder Note plugin choice (template)