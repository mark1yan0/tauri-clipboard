# Tauri Clipboard

### In Developemnt

This is my first Tauri App.
Since i haven't found a clipboard manager app for macOS that i was happy with, i decided to try a build my own using Tauri

Tauri is an awsome tool that allows us to build performant Desktop Application using any web tool we like to the frontend and Rust for the backend.

Since i'm a Frontend developer (with some backend knoledge), it decided to git it a try and chose a frontend framework i've never used, SvelteJS. For far I like the expirience

I've never used Rust, but I think this i a greak opportunity to try and learn somethink new, both the frontend (as mentioned above, Svelte) and for a new language

This app is still in active development

# TODO

Limitation: only reads the last copied item

## MWP v0.1.0-alpha

Base app to work

- [x] get clipboard content
- [x] delete item with btn
- [x] update list button
  - [ ] auto update on global copy event
- [x] save list locally
- [x] retrieve local list on mount
- [x] menu bar
- [ ] remove icon from apps bar
- [ ] lose focus on a selected item (hide window)
- [ ] add clear all button
- [x] clicking on an item makes it current copy
  - [x] current copy should not be added to list when copied
- [ ] toggle app on key shortcut
  - [x] register shortcut "command + b"
  - [ ] give possibility to decide the key shortcut to register the first time
- [ ] open on system startup
- [ ] add keyboard navigation (tabs for delete btn, arrow keys for items)
- [ ] definitive styling
- [ ] refactor

## Extra

- [ ] auto update list on copy/cut from system
- [ ] move key shortcut to Rust layer
- [ ] bulk edit
- [ ] user settings
- [ ] more
- [ ] add a build configuration roadmap file
  - [ ] identifier
  - [ ] platforms
  - [ ] build method
  - [ ] distrubution
  - [ ] update within the app
  - [ ] cross compilation?

Special Thanks to:
https://betterprogramming.pub/create-menubar-app-with-tauri-510ab7f7c43d
