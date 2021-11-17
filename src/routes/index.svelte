<ShowController />

{#if $store.full}
<Slideshow/>
{:else}
<div class="speaker">
  <div class="deck pane">
    <Slideshow />
  </div>
  <div class="note pane">
    <Notes />
  </div>
</div>
{/if}

<script>
  import { setContext } from 'svelte'
  import { writable } from 'svelte/store'
  import key from '$lib/key.js'
  import slides from '$lib/slides/slides.js'

  import ShowController from '$lib/ShowController.svelte'
  import Slideshow from '$lib/Slideshow.svelte'
  import Notes from '$lib/Notes.svelte'

  const store = writable({
    full: true,
    index: 0,
    slides
  })

  setContext(key, store)
</script>

<style>
  .speaker {
    display: flex;
    justify-content: space-evenly;
    width: 100%;
  }

  .pane {
    display: flex;
    width: 50%;
    box-sizing: border-box;
  }
</style>