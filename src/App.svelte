<script>
  import Header from "./Layouts/Header.svelte";
  import Section from "./Layouts/Section.svelte";
  import Gallery from "./UI/Gallery.svelte";
  import Hero from "./UI/Hero.svelte";
  import Slideshow from "./UI/Slideshow.svelte";

  let page = "steam";
  let isSlideshowOpen = false;

  const toggleView = () => (isSlideshowOpen = !isSlideshowOpen);
</script>

<Header
  background="white"
  linkColor="#333"
  on:pagenav={(e) => (page = e.detail)} />

<Hero
  title="Student Galleries"
  background="https://myfunscience.com/wp-content/uploads/plant-bg3.jpg"
  height="200px"
  color="white">
  <button on:click={toggleView}>Toggle View</button>
</Hero>

{#if page === 'steam'}
  <Section background="#307ad5" padding="2em 0">
    {#if !isSlideshowOpen}
      <Gallery
        source="https://public-api.wordpress.com/rest/v1.1/sites/repo995752852.wordpress.com/posts/?category=steam"
        title="STEAM Club"
        color="white" />
    {:else}
      <Slideshow
        source="https://public-api.wordpress.com/rest/v1.1/sites/repo995752852.wordpress.com/posts/?category=steam" />
    {/if}
  </Section>
{/if}

{#if page === 'art'}
  <Section background="white" padding="2em 0">
    {#if !isSlideshowOpen}
      <Gallery
        source="https://public-api.wordpress.com/rest/v1.1/sites/repo995752852.wordpress.com/posts/?category=art-class"
        title="Art Class"
        color="#307ad5" />
    {:else}
      <Slideshow
        source="https://public-api.wordpress.com/rest/v1.1/sites/repo995752852.wordpress.com/posts/?category=art-class" />
    {/if}
  </Section>
{/if}

<style>
  button {
    margin-bottom: 2em;
    background: #fdc735;
    color: #202020;
    padding: 1em 2em;
    border: none;
    outline: none;
    border-radius: 25px;
  }
</style>
