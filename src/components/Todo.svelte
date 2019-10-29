<script>
	import { createEventDispatcher } from 'svelte';
	const dispatch = createEventDispatcher();

  export let item;

  function remove() {
    dispatch('remove', { id: item.id });
  }
</script>

<div class="todo-item">
  <label class:done={item.checked}>
    <input type=checkbox bind:checked={item.checked}>{item.text}
  </label>
  <span class="remove" on:click={remove}>x</span>
</div>

<style>
.todo-item {
  display: flex;
  align-items: center;
}
.todo-item label {
  user-select: none;
  display: flex;
  align-items: center;
}
.todo-item label input[type="checkbox"] {
  margin:  0 5px 0 0;
}
.todo-item .done {
  opacity: 0.4;
  text-decoration: line-through;
}
.todo-item .remove {
  color: tomato;
  margin-left: 5px;
  cursor: pointer;
}
</style>