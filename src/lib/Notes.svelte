<div class="noteshow">
  <svelte:component this={$store.slides[$store.index]}></svelte:component>
  <span class="pagination">
    {$store.index + 1} / {$store.slides.length}
  </span>
</div>

<script>
  import key from './key.js'
  import { getContext } from 'svelte'
  const store = getContext(key)
</script>

<style>
  .noteshow {
    width: 100%;
  }
</style>