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
  color="#fdc735" />

{#if page === 'steam'}
  <Section padding="2em" title="STEAM Club" titleColor="white" align="left">
    <Gallery
      source="https://public-api.wordpress.com/rest/v1.1/sites/repo995752852.wordpress.com/posts/" />
  </Section>
{/if}

{#if page === 'art'}
  <Section
    background="white"
    padding="2em"
    title="Art Class"
    titleColor="#307ad5"
    align="left">
    <Gallery
      source="https://public-api.wordpress.com/rest/v1.1/sites/repo995752852.wordpress.com/posts/" />
  </Section>
{/if}

{#if page === 'webdev'}
  <Section
    background="#202020"
    padding="2em"
    title="Web Development"
    titleColor="white"
    align="left">
    <Gallery
      source="https://public-api.wordpress.com/rest/v1.1/sites/repo995752852.wordpress.com/posts/" />
  </Section>
{/if}
