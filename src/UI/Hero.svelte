<script>
  export let boxed = false;
  export let push = false;
  export let full = false;
  export let title = "";
  export let color = "white";
  export let background = "";
  export let height = "600px";
</script>

<aside
  class:boxed
  class:full
  style="background: url({background}) no-repeat center center/cover;background-repeat: no-repeat;min-height:{height};">
  <div class:push style="color:{color};">{title}</div>
  <slot />
</aside>

<style>
  aside {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 100%;
    background-position: center center;
  }
  aside div {
    max-width: 960px;
    margin: 0 auto;
    padding: 2rem;
    font-size: 4rem;
    line-height: 1.2em;
    font-weight: 700;
    color: white;
    text-shadow: 1px 0 10px rgba(0, 0, 0, 0.5);
    text-transform: uppercase;
    text-align: center;
  }
  .push {
    margin-top: 1em;
  }
  .full {
    min-height: 100vh;
  }
</style>
