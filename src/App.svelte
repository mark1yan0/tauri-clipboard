<script lang="ts">
  import ClipboardList from './lib/ClipboardList.svelte';
  import { register } from '@tauri-apps/api/globalShortcut';
  import { appWindow } from '@tauri-apps/api/window';

  // TODO should be done on Rust layer
  // issue: if not opened the first time from the menu bar, will be centered
  // best way to solve is to move to Rust layer
  register('Cmd+B', async () => {
    if (await appWindow.isVisible()) {
      await appWindow.hide();
    } else {
      await appWindow.show();
      await appWindow.setFocus();
    }
  });
</script>

<main class="container">
  <h1 class="title">Clipboard</h1>

  <ClipboardList />
</main>

<style>
  .container {
    padding: 1em;
  }

  .title {
    margin-bottom: 1rem;
  }
</style>
