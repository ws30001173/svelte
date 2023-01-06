<script>
  // Event modifiers:
  // once - makes sure the event can only fire once (removes handler)
  // preventDefault - prevent the default action (run e.preventDefault())
  // self - only fires the event if the clicked element is the target
  import Modal from './Modal.svelte';
  import AddPersonForm from './AddPersonForm.svelte';

  // override the showModal props
  let showModal = false;

  const toggleModal = () => {
    showModal = !showModal;
  }

  let people = [
    { name: 'yoshi', beltColor: 'black', age: 25, skills: 'fighting', id:1 },
    { name: 'mario', beltColor: 'red', age: 30, skills: 'swimming', id: 2},
    { name: 'luigi', beltColor: 'purple', age: 30, skills: 'running', id:3}
  ];

  const handleClick = (id) => {
    people = people.filter((person) => person.id != id);
  }

  // event prameter
  const addPerson = (e) => {
    const person = e.detail;
    people = [person, ...people];
    console.log(e.detail);
    console.log(people);

    showModal = false;
  }

  let num = 20;

</script>

<!-- <Modal message="Hey I am a prop value" isPromo=(true)/> -->
<!-- event forwarding -->
<!-- slot -->
<!-- after clicking -->
<Modal showModal={showModal} on:click={toggleModal}>
  <!-- // listen to custom event -->
  <AddPersonForm on:addPerson={addPerson}/>
</Modal>


{#if num > 15} 
  <h3 class="Shishou">Hello Shishou~</h3>
{:else if num > 10}
  <p>num greater than 10</p> 
{:else}
  <p>num less or equal than 10</p>
{/if}
<main>
  <!-- // Clicking to open  -->
  <button on:click|once={toggleModal}>open modal</button>
  {#each people as person}
  <div>
    <h4>{person.name}</h4>
    {#if person.beltColor == 'black'}
      <p><strong>master ninja</strong></p>
    {/if}
    <p>{person.age} years old, {person.beltColor} belt</p>
    <p>His skill is {person.skills}</p>
    <button on:click={handleClick(person.id)}>delete</button>
  </div>
  {:else}
    <p>no people to show</p>
  {/each}

</main>

<!-- component specific style by using unique classes -->
<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
