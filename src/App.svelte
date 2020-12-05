<script>
  import Header from "./Layouts/Header.svelte";
  import Section from "./Layouts/Section.svelte";
  import Gallery from "./UI/Gallery.svelte";
</script>

<Header background="white" linkColor="#333" />

<Section padding="2em" title="STEAM Club" titleColor="white">
  <Gallery
    source="https://public-api.wordpress.com/rest/v1.1/sites/repo995752852.wordpress.com/posts/" />
</Section>
