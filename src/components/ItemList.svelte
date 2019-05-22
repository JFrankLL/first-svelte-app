<script>
  import Item from "./Item.svelte";

  export let items;
</script>

<style>
  div.item-list {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    padding: 22px;
    margin-top: 22px;
    grid-gap: 18px;
  }
</style>

<div class="item-list">
  {#each items as item}
    <Item {...item} />
  {:else}
    <span>No items</span>
  {/each}
</div>
