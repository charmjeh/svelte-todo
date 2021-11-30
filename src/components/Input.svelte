<script>
  import { onMount } from 'svelte';

  export let todo;
  export let addTodo;
  export let handleKeyUp;
  export let ref;

  onMount(() => {
    ref.focus();
  })
</script>

<div>
  <input type="text" placeholder="할일을 입력해주세요" bind:value={todo} on:keyup={e => handleKeyUp(e)} bind:this={ref}/>
  <button on:click={addTodo}>ADD</button>
</div>

<style>
div {
  margin-bottom: 15px;
  display: flex;
}

input,
button {
  padding: 10px 20px;
  border-radius: 4px;
}

input {
  flex: none;
}

button {
  margin-left: auto;
  background: #4294e3;
  color: white;
}
</style>