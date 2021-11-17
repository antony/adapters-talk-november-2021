<div class="slide alt1">
  <h4>What are adapters for?</h4>

  <img src={adaptersImage} alt="adapters" />

  <h5>Adapters</h5>
  <ul>
    <li>Clear out the build dir</li>
    <li>Builds a lambda</li>
    <li>Prerender pages</li>
    <li>Shim fetch</li>
    <li>Bundle modules</li>
    <li>Organise the filesystem</li>
  </ul>
</div>

<ul class="notes">
  <li>A lot of "serverless" providers exist</li>
  <li>entire existence is around optimising developer experience and performance</li>
  <li>all the same, all use AWS under the hood, but all do things slightly differently</li>
  <li>Svelte adapters take your application's bundle and optimise it for deployment somewhere</li>
  <li>Usually build a lambda which translates to and from SvelteKit's request/response format</li>
</ul>

<script>
  import adaptersImage from './adapters.svg'
</script>

<style>
  img {
    margin: auto 0;
  }
</style>