<script>
  export let title = "Title";
  export let content = "Enter your content as text or html.";
  export let center = false;
  export let raise = false;
  export let blur = false;
  export let fx = false;
  export let ribbon = false;
  export let metal = false;
</script>

<main class:metal class:raise>
  <h1 class:blur class:ribbon class:fx contenteditable><span>{title}</span></h1>
  <p class:center>
    <span contenteditable>{@html content}</span>
  </p>
</main>

<style>
  main {
    margin: 2rem 0;
    padding: 2rem;
    background: white;
    border-radius: 4px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.24);
  }
  span {
    display: inline-block;
    padding: 1rem;
    border-radius: 4px;
  }
  h1 {
    display: flex;
    align-items: center;
    justify-content: center;
    margin: 0;
    color: #555;
    font-size: 2.5rem;
    line-height: 1em;
  }
  h1.ribbon::before,
  h1.ribbon::after {
    content: "";
    display: flex;
    flex: 1;
    height: 2rem;
  }

  h1.fx::before,
  h1.fx::after {
    animation: fx 3s infinite alternate-reverse ease-in-out;
  }

  h1.blur::before,
  h1.blur::after {
    filter: blur(10px);
  }

  .raise {
    box-shadow: 0px 30px 20px rgba(0, 0, 0, 0.25);
  }

  .center {
    text-align: center;
  }

  .metal {
    background-image: linear-gradient(
      to bottom,
      transparent,
      rgba(0, 0, 0, 0.1)
    );
  }

  @keyframes fx {
    from {
      filter: blur(0px);
    }
    to {
      filter: blur(20px);
    }
  }

  h1::before {
    background: linear-gradient(to right, #606c88, #3f4c6b);
    border-top-left-radius: 4px;
    border-bottom-left-radius: 4px;
  }
  h1::after {
    background: linear-gradient(to left, #606c88, #3f4c6b);
    border-top-right-radius: 4px;
    border-bottom-right-radius: 4px;
  }
  h1 span {
    text-align: center;
  }
  p {
    color: #555;
    line-height: 1.4em;
    margin: 0;
  }
</style>
