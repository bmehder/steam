<script>
  import Section from "./Layouts/Section.svelte";
  import Header from "./Layouts/Header.svelte";
  import Gallery from "./UI/Gallery.svelte";
</script>

<div class="wrapper">
  <Header background="white" linkColor="#333" />

  <Section padding="2em" title="STEAM Club" titleColor="white">
    <Gallery
      source="https://public-api.wordpress.com/rest/v1.1/sites/repo995752852.wordpress.com/posts/" />
  </Section>
</div>

<style>
  .wrapper {
    display: grid;
    grid-template-rows: auto 1fr auto;
    min-height: 100vh;
  }
</style>
