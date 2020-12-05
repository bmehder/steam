<script>
  export let shadow = false;
</script>

<blockquote class:shadow>
  <slot />
</blockquote>

<style>
  blockquote {
    background: #f9f9f9;
    border-left: 10px solid #f06;
    margin: 2em 10px 3em;
    padding: 2em;
    quotes: "\201C""\201D""\2018""\2019";
  }
  blockquote:before {
    color: #ccc;
    content: open-quote;
    font-size: 4em;
    line-height: 0.1em;
    margin-right: 0.25em;
    vertical-align: -0.4em;
  }
  .shadow {
    box-shadow: 0 20px 40px rgba(0, 0, 0, 0.24);
  }
</style>
