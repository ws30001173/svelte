<script>
  export let name;
  let beltColor = 'black belt';

  const handleClick = () => {
    beltColor = 'orange belt';
  }

  console.log("Hello~");
</script>

<main>
  <h1>Morning {name}!</h1>
  <p>{beltColor}</p> 
  <button on:click={handleClick}>update belt color</button>
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
