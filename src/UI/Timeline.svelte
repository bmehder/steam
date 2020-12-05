<script>
  export let data = [];
</script>

<main>
  <div class="timeline">
    <!-- Choose variables from properties -->
    {#each data as { year, name, src }, i}
      <div class="container {i % 2 === 0 ? 'left' : 'right'}">
        <div class="content">
          <!-- Create template using above variables-->
          <figure><img {src} alt={name} /></figure>
          <article>
            <h2>{year}</h2>
            <p>{name}</p>
          </article>
          <!-- End custom template -->
        </div>
      </div>
    {:else}
      <!-- Fallback if no data -->
      <div class="container">
        <div class="content">No data available.</div>
      </div>
    {/each}
  </div>
  <!-- The code displayed on screen. -->
  <!-- <section>
    <code>
      <pre>{JSON.stringify(data, null, 2)}</pre>
    </code>
  </section> -->
</main>

<style>
  main {
    max-width: 960px;
    margin: auto;
  }

  /* The actual timeline (the vertical ruler) */
  .timeline {
    position: relative;
    max-width: 1200px;
    margin: 0 auto;
  }

  /* The actual timeline (the vertical ruler) */
  .timeline::after {
    content: "";
    position: absolute;
    width: 6px;
    background-color: white;
    top: 0;
    bottom: 0;
    left: 50%;
    transform: translateX(-3px);
    box-shadow: 0px 20px 40px rgba(0, 0, 0, 1);
  }

  /* section {
    background: white;
    max-width: 960px;
    margin: 60px auto;
    padding: 20px;
    overflow-x: scroll;
    border-radius: 6px;
  } */

  /* Media queries - Responsive timeline on screens less than 600px wide */
  @media screen and (max-width: 600px) {
    /* Place the timelime to the left */
    .timeline::after {
      left: 31px;
    }
  }
  /* Container around content */
  .container {
    padding: 10px 40px;
    position: relative;
    background-color: inherit;
    width: 50%;
  }

  /* The circles on the timeline */
  .container::after {
    content: "";
    position: absolute;
    width: 25px;
    height: 25px;
    right: -17px;
    background-color: white;
    border: 4px solid #ff9f55;
    top: 15px;
    border-radius: 50%;
    z-index: 1;
  }

  /* Place the container to the left */
  .left {
    left: 0;
  }

  /* Place the container to the right */
  .right {
    left: 50%;
  }

  /* Add arrows to the left container (pointing right) */
  .left::before {
    content: " ";
    height: 0;
    position: absolute;
    top: 22px;
    width: 0;
    z-index: 1;
    right: 30px;
    border: medium solid white;
    border-width: 10px 0 10px 10px;
    border-color: transparent transparent transparent white;
  }

  /* Add arrows to the right container (pointing left) */
  .right::before {
    content: " ";
    height: 0;
    position: absolute;
    top: 22px;
    width: 0;
    z-index: 1;
    left: 30px;
    border: medium solid white;
    border-width: 10px 10px 10px 0;
    border-color: transparent white transparent transparent;
  }

  /* Fix the circle for containers on the right side */
  .right::after {
    left: -16px;
  }

  /* The actual content */
  .content {
    display: flex;
    padding: 20px 30px;
    background-color: white;
    position: relative;
    border-radius: 6px;
    box-shadow: 0px 20px 40px rgba(0, 0, 0, 0.24);
  }
  article {
    margin-left: 31px;
  }
  figure {
    margin: 0;
    padding: 0;
  }
  img {
    width: 80px;
    height: 80px;
    object-fit: cover;
    box-shadow: 0px 20px 40px rgba(0, 0, 0, 0.24);
    border-radius: 50%;
  }
  h2 {
    margin: 0;
  }
  p {
    font-weight: bold;
  }
  /* Media queries - Responsive timeline on screens less than 600px wide */
  @media screen and (max-width: 600px) {
    /* Full-width containers */
    .container {
      width: 100%;
      padding-left: 70px;
      padding-right: 25px;
    }

    /* Make sure that all arrows are pointing leftwards */
    .container::before {
      left: 60px;
      border: medium solid white;
      border-width: 10px 10px 10px 0;
      border-color: transparent white transparent transparent;
    }

    /* Make sure all circles are at the same spot */
    .left::after,
    .right::after {
      left: 15px;
    }

    /* Make all right containers behave like the left ones */
    .right {
      left: 0%;
    }
  }
</style>
