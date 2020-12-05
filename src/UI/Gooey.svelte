<script>
  import { fly } from "svelte/transition";
</script>

<section in:fly={{ duration: 600, x: 1000, y: 0, opacity: 0.5 }}>
  <!-- <h3>Gooey SVG Spinner</h3> -->
  <svg>
    <filter id="gooey">
      <feGaussianBlur in="SourceGraphic" stdDeviation="10" />
      <feColorMatrix values=" 1 0 0 0 0 0 1 0 0 0 0 0 1 0 0 0 0 0 20 -10" />
    </filter>
  </svg>
  <div class="loader">
    <span style="--i:1;" />
    <span style="--i:2;" />
    <span style="--i:3;" />
    <span style="--i:4;" />
    <span style="--i:5;" />
    <span style="--i:6;" />
    <span style="--i:7;" />
  </div>
</section>

<style>
  /* h3 {
    color: darkorange;
  } */
  section {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    /* background: #000; */
  }
  .loader {
    position: relative;
    width: 200px;
    height: 200px;
    filter: url(#gooey);
  }
  .loader span {
    position: absolute;
    width: 100%;
    height: 100%;
    display: block;
    animation: animate 4s ease-in-out infinite;
    animation-delay: calc(0.2s * var(--i));
  }
  .loader span:before {
    content: "";
    position: absolute;
    top: 0;
    left: calc(50% - 20px);
    width: 40px;
    height: 40px;
    border-radius: 50%;
    background: #9bdc28;
    box-shadow: 0 0 30px #03a9f4;
    background: linear-gradient(#fce4ec, #03a9f4);
  }
  @keyframes animate {
    0% {
      transform: rotate(0deg);
    }
    50%,
    100% {
      transform: rotate(360deg);
    }
  }
  svg {
    width: 0;
    height: 0;
  }
</style>
