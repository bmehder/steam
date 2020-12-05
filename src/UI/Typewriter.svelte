<script>
  import { onMount } from "svelte";
  import { fade, fly } from "svelte/transition";

  // Props
  export let phrase = "Hello World!";
  export let speed = 100;
  export let audioNo = 3;

  let typedChars = "";
  let index = 0;
  let typewriter;
  let finished;

  const typingSFX = [
    "https://assets.codepen.io/504854/type_1.mp3",
    "https://assets.codepen.io/504854/type_2.mp3",
    "https://assets.codepen.io/504854/type_3.mp3",
  ];

  const playSFX = () => {
    let url = typingSFX[audioNo - 1];
    let keySFX = new Audio(url);

    keySFX.play();
  };

  const typeChar = () => {
    if (index < phrase.length) {
      finished = false;
      // playSFX();
      typedChars += phrase[index];
      index += 1;
    } else {
      clearInterval(typewriter);
      finished = true;
      index = 0;
    }
  };

  const typing = () => (typewriter = setInterval(typeChar, speed));

  const replay = () => {
    typedChars = "";
    typing();
  };

  onMount(() => typing());
</script>

<section in:fly={{ duration: 600, x: 1000, y: 0, opacity: 0.5 }}>
  <figure>
    {#if !finished}
      <img
        in:fly={{ duration: 600, x: 0, y: 1000, opacity: 0.5 }}
        out:fly={{ duration: 2000, x: 0, y: -1000, opacity: 0.5 }}
        src="./assets/dolphin.png"
        alt="" />
    {/if}
  </figure>
  <h1>{typedChars}</h1>
  {#if finished}
    <button in:fly={{ y: -200, duration: 600 }} on:click={replay}>
      &#8634;
    </button>
  {/if}
</section>

<style>
  section {
    position: relative;
    width: 100%;
    min-height: 500px;
    display: flex;
    flex-direction: column;
    justify-content: start;
    align-items: center;
    color: white;
  }
  h1 {
    height: 3em;
    font-family: "Special Elite", cursive;
    font-size: 4em;
    line-height: 1.5em;
    width: 80%;
    text-shadow: 16px 32px 64px rgba(0, 0, 0, 1);
  }
  button {
    position: absolute;
    top: 1em;
    right: 2em;
    width: 60px;
    height: 60px;
    font-weight: bold;
    font-size: 2em;
    line-height: 1em;
    border-radius: 50%;
    background: darkorange;
    border: none;
    box-shadow: 16px 32px 64px rgba(0, 0, 0, 1),
      -16px -32px 64px rgba(255, 255, 255, 0.6);
    transition: 500ms;
  }
  button:hover {
    box-shadow: 16px 32px 64px rgba(0, 0, 0, 0.8),
      -16px -32px 64px rgba(255, 255, 255, 0.6);
    transform: scale(0.95);
  }
  figure {
    height: 100px;
  }
  img {
    width: 250px;
    height: auto;
  }
</style>
