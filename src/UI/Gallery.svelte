<script>
  import { scale } from "svelte/transition";
  import Grid from "../Layouts/Grid.svelte";

  export let source;

  // Create an empty array for the posts
  let posts = [];

  $: posts.length !== 0 ? console.log(posts[postIndex]) : undefined;

  // Is the modal open?
  let isModalOpen = false;

  // Create a variable to hold the Promise
  let promise = (url) => getData(url);

  // Function to get the data using the Fetch API
  async function getData(url) {
    const res = await fetch(url);
    // Turn the response into a JS object
    const data = await res.json();
    // If all is well with the data, put it in the array, and return it.
    if (res.ok) {
      posts = [...data.posts];
      return posts; // An array of objects representing posts
    } else {
      throw new Error(posts);
    }
  }

  // Keep track of the index of the post that was clicked on.
  let postIndex = 0;

  const updatePostIndex = (index) => {
    postIndex = index;
    isModalOpen = true;
    // console.log(postIndex);
  };

  const closeModal = () => {
    isModalOpen = false;
  };
</script>

<!-- Asynchronously get the posts by invoking the "promise" variable -->
{#await promise(source) then posts}
  <!-- <p>...waiting</p> -->

  <!-- Once the Promise is resolved (successfully)... -->
  <!-- {:then} -->
  {#if !isModalOpen}
    <Grid columns="1fr 1fr 1fr" gap="2em">
      <!-- 	Loop through each post... -->
      {#each posts as post, i}
        <!-- 		Use the featured image property of the current object as the src attribute -->
        <a href="/"><img
            in:scale
            on:click|preventDefault={(e) => updatePostIndex(i)}
            src={post.featured_image}
            alt="gallery-item" /></a>
      {/each}
    </Grid>
  {:else}
    <div transition:scale class="modal" on:click={closeModal}>
      <img src={posts[postIndex].featured_image} alt="single item" />
    </div>
  {/if}
  <!-- ...Or, if the Promise is rejected, handle the error -->
{:catch error}
  <p>Something has gone horribly wrong. :-(</p>
  <p style="color: red">{error.message}</p>

  <!-- End Async request -->
{/await}

<style>
  img {
    display: block;
    margin: 1em auto;
    width: 250px;
    height: 250px;
    object-fit: cover;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.24);
  }

  .modal {
    position: absolute;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    top: 0;
    left: 0;
    width: 100%;
    height: 100vh;
    background-color: rgba(0, 0, 0, 0.9);
  }
  .modal img {
    width: auto;
    height: 80%;
  }

  @media screen and (max-width: 600px) {
    img {
      width: 90% !important;
      margin: 2em auto;
    }
  }
</style>