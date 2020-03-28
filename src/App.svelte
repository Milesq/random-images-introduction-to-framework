<script>
  import Controler from './components/Controller.svelte';
  import { onMount } from 'svelte';
  import Macy from 'macy';

  onMount(() => {
    new Macy({
      container: '.macy-container',
      margin: {
        x: 20,
        y: 30
      },
      columns: 6
    });
  });

  let imgCount = 20;
  $: images = new Array(imgCount).fill().map((el, i) => {
    const w = Math.random() * 150 + 150;
    const h = Math.random() * 100 + 250;

    return [`https://picsum.photos/${Math.round(w)}/${Math.round(h)}`, i];
  });
</script>

<main>
  <div class="controller-container">
    <div>Ile obrazków chcesz wyświetlić?</div>
    <Controler bind:value="{imgCount}" />
  </div>

  <div class="macy-container">
    {#each images as url (url[1])}
      <img src="{url[0]}" alt="" />
    {/each}
  </div>
</main>

<style>
  .controller-container {
    display: flex;
    padding: 50px;
    align-items: center;
    flex-direction: column;
  }

  .macy-container {
    margin: 50px;
  }

  img {
    user-select: none;
  }
</style>
