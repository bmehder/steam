<script>
  import Header from "./Layouts/Header.svelte";
  import Section from "./Layouts/Section.svelte";
  import Gallery from "./UI/Gallery.svelte";
  import Hero from "./UI/Hero.svelte";

  let page = "steam";
</script>

<Header
  background="white"
  linkColor="#333"
  on:pagenav={(e) => (page = e.detail)} />

<Hero
  title="Student Galleries"
  background="https://source.unsplash.com/random/"
  height="200px"
  color="white" />

{#if page === 'steam'}
  <Section background="#307ad5" padding="2em" titleColor="white" align="left">
    <Gallery
      source="https://public-api.wordpress.com/rest/v1.1/sites/repo995752852.wordpress.com/posts/"
      title="STEAM Club"
      color="#fdc735" />
  </Section>
{/if}

{#if page === 'art'}
  <Section background="white" padding="2em" titleColor="#307ad5" align="left">
    <Gallery
      source="https://public-api.wordpress.com/rest/v1.1/sites/repo995752852.wordpress.com/posts/"
      title="Art Class"
      color="#307ad5" />
  </Section>
{/if}

{#if page === 'webdev'}
  <Section background="#202020" padding="2em" titleColor="#fdc735" align="left">
    <Gallery
      source="https://public-api.wordpress.com/rest/v1.1/sites/repo995752852.wordpress.com/posts/"
      title="Web Development"
      color="#fdc735" />
  </Section>
{/if}
