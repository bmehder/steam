<script>
  export let heading = "Heading";
  export let subtitle = "Lorem ipsum dolor sit amet.";
  export let href = "";
  export let src = "https://source.unsplash.com/random/300x250";
  export let buttonText = "Learn More";
  export let swap = false;
</script>

<article>
  <div>
    <h3>{heading}</h3>
    <p>{subtitle}</p>
    <a {href} target="_blank"> {buttonText} </a>
  </div>
  <figure class:swap><img {src} alt="placeholder" /></figure>
</article>

<style>
  article {
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 600px;
    height: 250px;
    margin: 2em auto;
    background: white;
    border-radius: 8px;
    box-shadow: 20px 30px 30px rgba(0, 0, 0, 0.25),
      10px 10px 60px rgba(255, 255, 255, 0.25) inset;
    background: #323232;
    background-image: linear-gradient(
      to bottom right,
      rgba(0, 0, 0, 0.1),
      rgba(0, 0, 0, 0.4)
    );
  }
  figure {
    margin: 0;
  }
  div {
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-evenly;
    padding: 2em;
    line-height: 1.25em;
    text-align: center;
    color: white;
  }
  h3 {
    margin: 0;
    font-size: 2em;
    color: gold;
  }
  p {
    font-weight: 600;
  }
  h3,
  p {
    text-shadow: 0px 0px 10px rgba(0, 0, 0, 0.25);
  }
  a {
    display: block;
    width: 100%;
    padding: 1em 2em;
    font-weight: bold;
    text-align: center;
    text-transform: uppercase;
    color: white;
    cursor: pointer;
    background: dodgerblue;
    box-shadow: 10px 10px 40px rgba(0, 0, 0, 0.5),
      2px 2px 4px rgba(255, 255, 255, 0.5) inset;
    border: none;
    border-radius: 5px;
    transition: 200ms;
  }
  a:hover {
    background: gold;
    color: #323232;
    text-decoration: none;
    box-shadow: 10px 10px 50px rgba(0, 0, 0, 0.5),
      2px 2px 4px rgba(255, 255, 255, 0.5) inset;
  }
  figure {
    width: 300px;
    height: 250px;
  }
  img {
    width: auto;
    height: 100%;
    border-top-right-radius: 8px;
    border-bottom-right-radius: 8px;
    object-fit: cover;
  }
  .swap {
    order: -1;
  }
  .swap img {
    border-top-right-radius: 0px;
    border-bottom-right-radius: 0px;
    border-top-left-radius: 8px;
    border-bottom-left-radius: 8px;
  }
</style>
