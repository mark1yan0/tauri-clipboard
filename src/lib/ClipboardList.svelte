<script lang="ts">
  import { readText, writeText } from '@tauri-apps/api/clipboard';
  import { onMount } from 'svelte';
  async function getClipboardText() {
    const clipboardText = await readText();
    return clipboardText;
  }

  // item interactions
  async function getCopy(payload: string) {
    await writeText(payload);
  }

  function removeItemFromList(_item: string) {
    const newItems = items.filter(item => item !== _item);
    persistList(newItems);
    items = newItems;
  }

  // update whole list
  async function addItemToList() {
    const text = await getClipboardText();

    if (items.includes(text)) {
      return;
    }

    const copiedArr = items;

    copiedArr.unshift(text);
    persistList(copiedArr);
    items = copiedArr;
  }

  // saves clipboard list locally
  function persistList(list: string[]) {
    localStorage.setItem('clipboard-list', JSON.stringify(list));
  }

  function getPersistedList() {
    const list = localStorage.getItem('clipboard-list');

    if (!list) {
      return [];
    }

    return JSON.parse(list);
  }

  let items: string[] = [];
  onMount(async () => {
    items = getPersistedList();

    // updates list with the newly copied value
    await addItemToList();
  });
</script>

<button class="update-btn" on:click={addItemToList}> Update </button>
<ul class="list">
  {#each items as item}
    <li class="item" on:click={() => getCopy(item)} on:keydown>
      {item}
      <button
        class="delete-button"
        on:click|stopPropagation={() => removeItemFromList(item)}
      >
        Delete
      </button>
    </li>
  {/each}
</ul>

<style>
  .update-btn {
    margin-bottom: 1rem;
  }

  .list {
    display: flex;
    flex-direction: column;
    gap: 1rem;
  }

  .item {
    list-style: none;
    padding: 2em;
    font-size: large;
    border: 3px solid var(--main-light);
    color: var(--text-light);
    border-radius: 0.5rem;
    transition: all 0.3s ease;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .item:hover {
    background-color: var(--main-light);
    color: var(--text-dark);
  }

  .item:focus {
    background-color: var(--main-light);
    color: var(--text-dark);
  }

  /* // todo: media prefers dark mode */
</style>
