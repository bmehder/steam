<script>
  import { fly } from "svelte/transition";
  import { cubicIn } from "svelte/easing";

  let ready = false;
  setTimeout(() => {
    ready = true;
  }, 0);
</script>

{#if ready}
  <main>
    <img
      transition:fly={{ duration: 800, x: 1000, easing: cubicIn }}
      src="https://myfunscience.com/wp-content/uploads/MyFunScience-logo-small.png"
      alt="MyFunScience Logo" />
    <div
      transition:fly={{ duration: 1000, x: -1000, easing: cubicIn }}
      class="square">
      <div><span>Technology</span></div>
      <div><span>Engineering</span></div>
      <div><span>Math</span></div>
      <div>Science</div>
    </div>
  </main>
{/if}

<!-- ################################################ -->
<style>
  @import url("https://fonts.googleapis.com/css2?family=Montserrat:wght@700&display=swap");
  main {
    position: relative;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    font-family: "Montserrat", sans-serif;
  }
  .square {
    margin-top: 60px;
    width: 250px;
    height: 250px;
    position: relative;
    perspective: 180px;
    color: white;
    font-weight: 700;
    text-shadow: 0 0 5px rgba(0, 0, 0, 0.5);
    filter: drop-shadow(0 20px 40px rgba(48, 122, 213, 0.12));
    animation: 8s spin linear alternate infinite;
  }
  .square div {
    position: absolute;
    display: flex;
    justify-content: center;
    align-items: center;
    top: 0;
    height: 125px;
    width: 125px;
    background: #10c45c;
    border-top-left-radius: 50%;
    animation: flip 8s ease-in-out infinite;
    transform-origin: right bottom -50px;
    box-shadow: 0 20px 40px rgba(48, 122, 213, 0.24);
    opacity: 0.9;
  }
  .square div:nth-child(2) {
    background: #fdc735;
    border-top-left-radius: 50%;
    animation-delay: 2s;
  }
  .square div:nth-child(3) {
    background: #d94da6;
    border-top-left-radius: 50%;
    border-top-right-radius: 0px;
    animation-delay: 4s;
  }
  .square div:nth-child(4) {
    background: #307ad5;
    border-top-left-radius: 50%;
    animation-delay: 6s;
  }
  /* .square div span {
    transform: rotateY(180deg);
  } */
  /* img {
    filter: drop-shadow(0 20px 40px rgba(0, 0, 0, 0.24));
  } */

  @keyframes flip {
    0% {
      transform: rotateX(0) rotateY(0);
    }
    25% {
      transform: rotateX(0) rotateY(180deg);
    }
    50% {
      transform: rotateX(180deg) rotateY(180deg);
    }
    75% {
      transform: rotateX(180deg) rotateY(0);
    }
    100% {
      transform: rotateX(0) rotateY(0);
    }
  }
  @keyframes spin {
    from {
      transform: rotate(0deg);
    }
    to {
      transform: rotate(180deg);
    }
  }
</style>
