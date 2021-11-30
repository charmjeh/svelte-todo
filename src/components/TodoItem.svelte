<script>
  export let todo;
  export let deleteTodo;
  export let handleComplete;

  $: checkboxClass = todo.completed ? 'checked' : '';
</script>

<div class="todo-item">
  <input bind:checked={checkboxClass} class="todo-item__checkbox" type="checkbox" on:change={()=> handleComplete(todo.id)}/>
  <span class="todo-item__content {checkboxClass}">{todo.text}</span>
  <button class="todo-item__submit"on:click={() => deleteTodo(todo.id)}>&#10006;</button>
</div>

<style> 
.todo-item {
  display: flex;
  padding: 5px 0;
}

.todo-item__checkbox {
  margin: 4px 10px 0 0;
}

.todo-item__checkbox,
.todo-item__content {
  flex: 0;
}

.todo-item__submit {
  margin: 0;
  margin-left: auto;
  padding: 0;
  background-color: transparent;
  border-radius: 50%;
  border: 0;
  color: red;
}

.checked {
  text-decoration: line-through;
  color: #999;
}
</style> 