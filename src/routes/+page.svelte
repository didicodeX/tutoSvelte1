<script>

  let todos = [
    { text: "Buy some milk", done: true },
    { text: "Learn Svelte", done: true },
    { text: "Read the docs", done: false },
  ];

  let todofield = '';

</script>

<!-- {JSON.stringify(todos)}

{todofield}

{#if active}
  <h1>Coucou</h1>
{:else}
  <h1>Bye</h1>
{/if} -->

<form
  on:submit|preventDefault={() => {
    todos = [
      ...todos,{
        number: todos.length + 1 ,
        text: todofield,
        done: false
      }
    ];
    todofield = '';

  }}
>
  <input type="text"  name="todo" id="todo" bind:value={todofield} />
  <button>Ajouter</button>
</form>

{#each todos as todo, i}
  <div>
    <input type="checkbox" name="done" id="done {i}" bind:checked={todo.done}>
    <label for="done {i}">{i+1}: {todo.text}</label>
    <button on:click={()=>{
      todos = todos.filter((t) => t !== todo)
    }}>X</button>
  </div>
{/each}

<style>

  label, button{
    cursor: pointer;
  }

</style>
