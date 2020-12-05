<script>
</script>

<div>
  <slot />
</div>

<style>
  div {
    display: flex;
    flex-direction: column;
    justify-content: space-evenly;
    align-items: center;
    width: 280px;
    height: 480px;
    margin: 1em;
    padding: 2em;
    background: white;
    border-radius: 10px;
    box-shadow: 0 20px 40px rgba(0, 0, 0, 0.24);
  }
</style>
