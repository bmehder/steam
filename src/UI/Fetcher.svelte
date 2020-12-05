<script>
  import { fly } from "svelte/transition";
  import Gooey from "./Gooey.svelte";
  export let endpoint =
    "https://raw.githubusercontent.com/bmehder/projects/master/json/covid.json";

  async function getData() {
    const res = await fetch(endpoint);
    const data = await res.json();
    // console.log(data);
    if (res.ok) {
      return data;
    } else {
      throw new Error(data);
    }
  }
  let promise = getData();
</script>

<section
  id="fetcher"
  class="carbon"
  in:fly={{ duration: 600, x: 1000, y: 0, opacity: 0.5 }}>
  {#await promise}
    <Gooey />
  {:then data}
    <!-- <h3>Async Data Fetcher</h3> -->
    <article class="heading shadow">
      <div><strong>Business</strong></div>
      <div><strong>Address</strong></div>
      <div><strong>Category</strong></div>
      <div><strong>Rating</strong></div>
    </article>
    {#each data as chunck, i}
      <article>
        <div>{chunck.business}</div>
        <div>{chunck.address}</div>
        <div>{chunck.cat}</div>
        <div>{chunck.rating}%</div>
      </article>
    {/each}
    <!-- <p>
      <small>
        <a
          href="https://raw.githubusercontent.com/bmehder/projects/master/json/covid.json"
          target="_blank">
          https://raw.githubusercontent.com/bmehder/projects/master/json/covid.json
        </a>
      </small>
    </p> -->
  {:catch error}
    <p>Something has gone horribly wrong. :-(</p>
    <p style="color: red">{error.message}</p>
  {/await}
</section>

<style>
  section {
    overflow-x: auto;
    padding-top: 0;
  }
  /* h3 {
    color: white;
  } */
  article {
    display: flex;
    /* min-width: 600px; */
  }
  article:nth-child(odd) {
    background-color: #fff;
  }
  article:nth-child(even) {
    background-color: #f1f1f1;
  }
  article div {
    width: 25%;
    line-height: 2em;
    padding: 1em 3em;
  }
  .heading {
    background-color: darkorange !important;
    color: #fff;
    margin-top: 50px;
  }
  p {
    display: flex;
    justify-content: center;
    margin: 1em 0;
    text-align: center;
  }
  a {
    color: darkorange;
    text-decoration: none;
  }
  a:hover {
    color: darkorange;
    border-bottom: 1px solid darkorange;
  }
</style>
