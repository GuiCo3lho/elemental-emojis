<script>
  import { getElement } from "../data/elements";
  import { fly } from "svelte/transition";

  let popovers = [];

  export const pop = (value) => {
    const data = { ...getElement(value), key: Math.random() + "" };
    popovers = [...popovers, data];

    setTimeout(() => {
      popovers = popovers.slice(1);
    });
  };
</script>

<style>
  span {
    position: absolute;
    font-size: 2em;
  }
</style>

{#each popovers as { emoji, key } (key)}
  <span out:fly={{ y: -40, duration: 700 }}> {emoji} </span>
{/each}
