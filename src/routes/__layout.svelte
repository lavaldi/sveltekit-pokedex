<script>
  import Nav from '../components/nav.svelte';
</script>

<div class="p-8 max-w-6xl mx-auto">
  <Nav />
  <slot />
</div>

<style>
  @tailwind base;
  @tailwind components;
  @tailwind utilities;

  :global(body) {
    background-image: url(/header-bg.png), url(/bg-squares.png);
    background-repeat: no-repeat, repeat;
  }
</style>
