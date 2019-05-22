<script>
  import { onMount, createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();

  import Button from "./Button.svelte";
  import Input from "./Input.svelte";

  export let schema;
  let values = init();

  function init() {
    return Object.entries(schema).reduce(
      (accumulator, current) => ({ ...accumulator, [current[0]]: null }),
      {}
    );
  }

  function resetForm() {
    values = Object.entries(values).reduce(
      (accumulator, current) => ({ ...accumulator, [current[0]]: null }),
      {}
    );
  }

  function onClickSubmitButton() {
    dispatch("submit", { ...values });
    resetForm();
  }
</script>

<style>
  div.form {
    display: flex;
    flex-direction: column;
    max-width: 344px;
    margin: auto;
  }
</style>

<div class="form">
  {#each Object.keys(schema) as key}
    <Input id={`i-${key}`} name={key} type={values[key]} bind:value={values[key]} />
  {/each}
  <Button on:click={onClickSubmitButton}>Submit</Button>
</div>
