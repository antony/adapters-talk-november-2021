<script>
  const code = `export {
        log,
        rimraf,
        mkdirp,
        copy,
        copy_client_files,
        copy_server_files,
        copy_static_files,
        prerender
      }`
</script>

<div class="slide alt0">
  <h4>Adapter Utils</h4>

  <h5>utils is passed into the adapter constructor.<br />it gives us a series of convenience functions:</h5>

  <pre>
    <span class="component-name">utils.js</span>
    {code.trim()}
  </pre>
</div>

<ul class="notes">
  <li>Utils functions for convenience</li>
  <li>special functions which predefine the source and destination dirs</li>
  <li>Logger for printing colour coded messages to the user</li>
  <li>Copy functions return a mini-manifest of files copied and locations - useful for routing configuration for various platforms</li>
</ul>

<style>
  pre {
    margin: auto 0;
    text-align: left;
  }
</style>