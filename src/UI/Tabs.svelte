<script>
  export let data;
  export let width = "";
  let dataIndex = 0;
  const chooseContent = (i) => (dataIndex = i);
</script>

<div class="wrapper">
  <div class="tab-headings" style="min-width:{width};">
    {#each data as { title }, i}
      <span class:active={dataIndex === i} on:click={() => chooseContent(i)}>
        {title}</span>
    {/each}
  </div>
  <article>{data[dataIndex].content}</article>
</div>

<style>
  .wrapper {
    margin: 2em auto;
    filter: drop-shadow(0 2px 4px rgba(0, 0, 0, 0.24));
  }
  .tab-headings {
    display: flex;
  }
  .tab-headings span {
    background: lightgray;
    padding: 1em 1.5em;
    border-right: 1px solid #f3f3f3;
    cursor: pointer;
  }
  .tab-headings .active {
    background: #f3f3f3;
  }
  article {
    background: #f3f3f3;
    padding: 1.5em;
    min-height: 10em;
  }
</style>
