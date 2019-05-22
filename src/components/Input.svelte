<script>
  export let id;
  export let type;
  export let name;
  export let value;
</script>

<style>
  label {
    text-transform: capitalize;
  }
</style>

<label for={id}>
  <strong> {name} </strong>
</label>
<input {id} {name} bind:value />
