<script>
  export let boxed = false;
  export let title = false;
  export let margin = "";
  export let padding = "";
  export let background = "";
  export let color = "";
  export let titleColor = "#555";
  export let align = "center";
</script>

<section
  class:boxed
  style="background:{background};color:{color};margin:{margin};padding:{padding};">
  <div class="content-wrap">
    {#if title}
      <h3 style="color:{titleColor};text-align:{align};">{title}</h3>
    {/if}
    <slot />
  </div>
</section>

<style>
  section {
    min-height: 100vh;
  }
  .boxed {
    max-width: 960px;
    margin: auto;
  }
  .content-wrap {
    max-width: 960px;
    margin: auto;
  }
  h3 {
    font-size: 3em;
    line-height: 1em;
    margin: 1em auto 1.5em;
    text-align: center;
  }
  @media screen and (max-width: 600px) {
    h3 {
      font-size: 1.5em;
    }
  }
</style>
