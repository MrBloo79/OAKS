OAKS (Obsidian Action and Knowledge System) is my proposal for an Obsidian powered second brain, of course developed with OAKS itself!

# Installation

1. Clone this repo and set it up as new vault (trust author)
2. Install recommended plugins (hijacking update feature)
    1. Install Screwdriver
    2. Switch to `Xtra/Required Plugins` file 
    3. Run `Screwdriver: Restore exported files from the active file` command
    4. Open Community plugins settings, check for updates and update all
3. Open Appearance settings, install recommended Minimal theme and turn on desired snippets
4. Set optional Git repository options

   ```bash
    git config core.autocrlf false # Obsidian works with LF only for now
    git config user.name <your name>
    git config user.email <your mail>
    ```

# Roadmap

## Features

- [ ] Quick capture (project, task, asset, date, link) [🏅:: 1]
- [ ] Quick edit [🏅:: 1]
- [ ] Advanced view (reusable, drill down-able, sortable, filterable) [🏅:: 1]
- [ ] Auto journaling [🏅:: 3]
- [ ] Custom templates (item, collection, issue link) [🏅:: 3]
- [ ] Better file management (folder note, attachment) [🏅:: 3]
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
- [x] Accent colored theme [🏅:: 3] ✅ 2023-12-11
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