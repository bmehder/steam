<script>
  export let shadow = false;
  export let uppercase = false;
  export let rounded = false;
  export let reflection = false;
  export let color = "white";
  export let background = "#f06";
  export let url = ".";
</script>

<a
  style="background:{background}; color:{color};"
  class:shadow
  class:uppercase
  class:rounded
  class:reflection
  href={url}
  target="_blank"><slot />
</a>

<style>
  a {
    display: inline-block;
    margin: 1.2em auto;
    padding: 1em 2em;
    font-weight: bold;
    border: none;
    border-radius: 5px;
    text-decoration: none;
    transition: 300ms;
    letter-spacing: 0.5px;
  }

  /* a:hover {
    transform: scale(0.98);
    transform-origin: center;
  } */

  .shadow {
    box-shadow: 0 8px 16px rgba(0, 0, 0, 0.25),
      0 8px 16px rgba(255, 255, 255, 0.25) inset;
  }
  .shadow:hover {
    box-shadow: 0 4px 4px rgba(0, 0, 0, 0.6),
      0 8px 16px rgba(255, 255, 255, 0.25) inset;
  }

  .uppercase {
    text-transform: uppercase;
  }

  .rounded {
    border-radius: 50px;
  }

  .reflection {
    -webkit-box-reflect: below 2px -webkit-gradient(linear, left top, left
          bottom, from(transparent), color-stop(50%, transparent), to(rgba(255, 255, 255, 0.2)));
  }
  .reflection:hover {
    -webkit-box-reflect: below 1px -webkit-gradient(linear, left top, left
          bottom, from(transparent), color-stop(50%, transparent), to(rgba(255, 255, 255, 0.17)));
  }
</style>
