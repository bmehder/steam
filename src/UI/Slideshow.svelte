<script>
  export let source;

  let posts = [];

  let promise = (url) => getData(url);

  async function getData(url) {
    const res = await fetch(url);
    const data = await res.json();
    if (res.ok) {
      posts = [...data.posts];
      return posts;
    } else {
      throw new Error(posts);
    }
  }

  let postIndex = 0;
  const goBack = () => (postIndex -= 1);
  const goForward = () => (postIndex += 1);
</script>

<article>
  {#await promise(source) then posts}
    <div>
      <button on:click|preventDefault={goBack} disabled={postIndex === 0}><i
          class="fa fa-2x fa-arrow-left" /></button>
      <img src={posts[postIndex].featured_image} alt="slideshow item" />
      <button
        on:click|preventDefault={goForward}
        disabled={postIndex === posts.length - 1}><i
          class="fa fa-2x fa-arrow-right" /></button>
    </div>
    <div>
      <p>
        {@html posts[postIndex].excerpt}
      </p>
    </div>
  {:catch error}
    <p>Something has gone horribly wrong. :-(</p>
    <p style="color: red">{error.message}</p>
  {/await}
</article>

<style>
  * {
    box-sizing: border-box;
  }
  article {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 600px;
    margin: auto;
  }
  article div {
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    margin: auto;
  }
  article p {
    width: 100%;
    margin: 0;
    padding: 1em;
    background: white;
  }
  img {
    width: 100%;
    object-fit: cover;
  }
  button {
    padding: 1em 2em;
    background: transparent;
    border: none;
    outline: none;
  }
  button:focus {
    outline: none;
  }

  @media screen and (max-width: 600px) {
    article {
      width: 80%;
    }
  }
</style>
