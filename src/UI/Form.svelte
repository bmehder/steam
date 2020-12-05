<script>
  export let title = "";
  export let titleColor = "";
  export let buttonColor = "";
  export let buttonText = "";
  export let buttonTextColor = "";
</script>

<div>
  <h3 style="color:{titleColor};">{title}</h3>
  <form>
    <input type="text" placeholder="Enter name..." />
    <input type="email" placeholder="Enter email..." />
    <textarea placeholder="Enter message..." />
    <button
      style="background:{buttonColor};color:{buttonTextColor};">{buttonText}</button>
  </form>
</div>

<style>
  h3 {
    margin: 1em;
    text-align: center;
  }
  form {
    display: flex;
    flex-direction: column;
    width: 400px;
    margin: 0 auto 4em;
  }
  input,
  textarea,
  button {
    margin: 0.5em 0;
    padding: 1em;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.24);
    border: none;
    outline: none;
  }
  textarea {
    min-height: 8em;
  }
  button {
    box-sizing: border-box;
    outline: none;
    border: none;
    font-weight: bold;
  }
</style>
