<script>
  let active = true;

  let todos = [
    { number: 1, text: "Buy some milk", done: true },
    { number: 2, text: "Learn Svelte", done: true },
    { number: 3, text: "Read the docs", done: false },
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
        number: todos.length + 1,
        text: todofield,
        done: false
      }
    ];
    todofield = '';
  }}
>
  <input type="text" name="todo" id="todo" bind:value={todofield} />
  <button>Ajouter</button>
</form>

{#each todos as todo}
  <div>
    <input type="checkbox" name="done" id="done {todo.number}" bind:checked={todo.done}>
    <label for="done {todo.number}">{todo.number}: {todo.text}</label>
    <button on:click={()=>{
      todos = todos.filter((t) => t.number !== todo.number)
    }}>X</button>
  </div>
{/each}

<style>

  label, button{
    cursor: pointer;
  }
  
</style>
