<script>
  const adapterCode = `export default function (options) {
  return {
    name: '@sveltejs/adapter-foo',

    async adapt({ utils }) {
      utils.log.minor('Generating serverless function...')
      utils.copy(join(files, 'entry.js'), '.svelte-kit/vercel/entry.js')

      utils.log.minor('Prerendering static pages...')
      await utils.prerender({
        dest: join(dir, 'static')
      })

      // here, we'd build the lambda - but it's pretty lengthy

      utils.log.minor('Copying assets...')
      utils.copy_static_files(join(dir, 'static'))
      utils.copy_client_files(join(dir, 'static'))

      utils.log.minor('Writing routes...')
      utils.copy(
        join(files, 'routes.json'),
        join(dir, 'config/routes.json')
      )
    }
  }
}`
</script>

<div class="slide alt2">
  <h4>How?</h4>

  <pre>
    <span class="component-name">adapter.js</span>
    {adapterCode.trim()}
  </pre>
</div>

<ul class="notes">
  <li>I wrote two adapters for the intial sveltekit release</li>
  <li>Adapters generally do two things - prerender - move files into the right place</li>
  <li>Adapters don't deal with actual physical deployment</li>
  <li>Some might write config files, manifests</li>
  <li>browser extension adapter creates shasums for the JS for security</li>
  <li>Simplified vercel adapter - no esbuild (which might get removed anyway)</li>
  <li>writes our special route handler</li>
  <li>writes static assets + client bundle</li>
  <li>tells vercel where to map paths to (routes.json)</li>
</ul>

<style>
  pre {
    text-align: left;
  }
</style>