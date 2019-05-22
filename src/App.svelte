<script>
  import Navbar from "./components/Navbar.svelte";
  import ItemForm from "./components/ItemForm.svelte";
  import ItemList from "./components/ItemList.svelte";

  let uuid = 1;

  let itemFormSchema = {
    name: { type: "" },
    description: { type: "" },
    price: { type: "" }
  };

  let items = [];

  function addItem(event) {
    items = items.concat({...event.detail, id: uuid++});
  }
</script>

<style>
  section {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .content {
    display: flex;
    justify-content: center;
    width: 100%;
    background-color: #ededed;
    min-height: 100%;
  }

  .content .content-wrapper {
    padding-top: 28px;
    max-width: 1000px;
    width: 100%;
    min-height: 100vh;
  }
</style>

<section>
  <Navbar name={''} />
  <div class="content">
    <div class="content-wrapper">
      <ItemForm schema={itemFormSchema} on:submit={addItem} />
      <ItemList {items} />
    </div>
  </div>
</section>
