<script>
  import Todo from './Todo.svelte';

  let todos = [
    {id: 0, text: 'Make TODO app', checked: true},
    {id: 1, text: 'Remake by store', checked: false},
    {id: 2, text: 'Make some tests', checked: false}
  ];
  let new_todo = '';

  function addTodo() {
    todos = todos.concat({id: new Date().getTime(), text: new_todo, checked: false});
    new_todo = '';
  }

  function remove(event) {
    let id = event.detail.id;

    todos = todos.filter(e => e.id !== id);
  }
</script>

<div class="todos">
  <form  on:submit|preventDefault={addTodo}>
    <input bind:value={new_todo}>
    <button type="submit">add</button>
  </form>

  {#each todos as td}
    <Todo item={td} on:remove={remove} />
  {/each}
</div>