<script>
  import { quintOut } from "svelte/easing";
  import { crossfade } from "svelte/transition";
  import { flip } from "svelte/animate";

  const [send, receive] = crossfade({
    duration: d => Math.sqrt(d * 200),

    fallback(node, params) {
      const style = getComputedStyle(node);
      const transform = style.transform === "none" ? "" : style.transform;

      return {
        duration: 348,
        easing: quintOut,
        css: t => `
          transform: ${transform} scale(${t});
          opacity: ${t}
        `
      };
    }
  });

  export let id;
</script>

<style>
  div {
    display: inline-block;
    background-color: #fff;
    padding: 22px;
    border-radius: 2px;
    box-shadow: 0 0 4px -4px black;
  }
</style>

<div in:receive={{ key: id }} out:send={{ key: id }}>Item</div>
