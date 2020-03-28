<script>
  export let value = 0;
  let inputMode = false;

  const changeMode = () => (inputMode = !inputMode);
  const dec = () => {
    if (value > 0) {
      --value;
    }
  };
  const inc = () => ++value;

  function blur() {
    if (value < 0) {
      value = Math.abs(value);
    }
  }
</script>

<div class="container">
  <button on:click="{dec}">-</button>
  <span on:dblclick="{changeMode}">
    {#if inputMode}
      <input type="number" on:blur="{blur}" min="0" bind:value />
    {:else}
      <span>{value}</span>
    {/if}
  </span>
  <button on:click="{inc}">+</button>
</div>

<style>
  .container {
    color: white;
  }
</style>
