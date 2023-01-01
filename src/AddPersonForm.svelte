<script>
  import { createEventDispatcher } from 'svelte';

  let dispatch = createEventDispatcher();

  let name;
  let beltColor;
  let age;
  let skills =[];

  const handleSubmit = () => {
    const person = {
      name,// can do "name: name," directly cause name the same
      beltColor,
      age,
      skills,
      id: Math.random()
    };
    dispatch('addPerson', person); // custom event
  };
</script>

<!-- submit form(on:click on button -->
<form on:submit|preventDefault={handleSubmit}>
    <input type="text" placeholder="name" bind:value={name}>
    <!-- <input type="text" placeholder="belt color" bind:value={beltColor}> -->
    <input type="number" placehodler="age" bind:value={age}>
    <label>Skills:</label>
    
    <input type="checkbox" bind:group={skills} value="fighting">fighting<br>
    <input type="checkbox" bind:group={skills} value="sneaking">sneaking<br>
    <input type="checkbox" bind:group={skills} value="running">running<br>

    <label>Belt color:</label>
    <select bind:value={beltColor}>
      <option value="black">black</option>
      <option value="orange">orange</option>
      <option value="brown">brown</option>
      <option value="white">white</option>
    </select>
    <button>Add Person</button>
</form>

<style>

</style>