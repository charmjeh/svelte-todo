<script>
	import Input from "./components/Input.svelte";
	import Todos from "./components/Todos.svelte";

	let todo = "";	// input에 입력될 값!
	let todoList = [
      {
        id: 1,
        text: "React",
        completed: false
      },
      {
        id: 2,
        text: "Vue",
        completed: true
      },
      {
        id: 3,
        text: "Svelte",
        completed: true
      }
	];
	
	let lastId = todoList[todoList.length-1]['id'];

	// 할일을 추가하는 함수
	let addTodo = () => {
      if(todo) {
        let newTodo = {
          id: ++lastId,
          text: todo,
          completed: false
        }

        todoList[todoList.length] = newTodo;
        todo = "";
      }
	}

  let deleteTodo = (id) => {
    todoList = todoList.filter((todo) => todo.id !== id);
  }

  let handleComplete = (id) => {
		const index = todoList.findIndex((todo) => todo.id === id);
		todoList[index]["completed"] = !todoList[index]["completed"];
	}
	
    // todo값을 업데이트 하면서, 엔터키를 누르면 할일이 추가되도록 하는 함수
	let handleKeyUp = e => {
		todo = e.target.value;
		if(e.keyCode === 13) {
			addTodo();
		}
	}
</script>

<main>
	<div class="card">
		<h1>To Do List</h1>
		<Input {todo} {addTodo} {handleKeyUp}/>
		<Todos {todoList} {deleteTodo} {handleComplete}/>
	</div>
</main>

<style>
main {
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: #f7f9fa;
  width: 100%;
  height: 100%;
}

.card {
  background-color: white;
  padding: 30px;
  width: 300px;
  border-radius: 3px;
}

h1 {
  text-align: center;
  margin: 0 0 20px 0;
}
</style>