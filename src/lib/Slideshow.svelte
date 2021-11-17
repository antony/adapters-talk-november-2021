<div class="slideshow">
  <svelte:component this={$store.slides[$store.index]}></svelte:component>
  <span class="pagination">
    {$store.index + 1} / {$store.slides.length}
  </span>
</div>

<script>
  import { browser } from '$app/env'
  import key from './key.js'
  import { getContext, onDestroy } from 'svelte'
  const store = getContext(key)

  const bcast = browser && new BroadcastChannel('svelte-present')

  bcast.onmessage = function (e) {
    console.log('message', e)
    const directions = {
      next: () => {
        const currentIndex = $store.index
        $store.index = currentIndex >= $store.slides.length - 1 ? currentIndex : currentIndex + 1
      },
      previous: () => {
        const currentIndex = $store.index
        $store.index = currentIndex < 1 ? currentIndex : currentIndex - 1
      }
    }
    directions[e.data] && directions[e.data]()
  }

  onDestroy(() => {
    bcast && bcast.close()
  })
</script>