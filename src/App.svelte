<script>
	import { onMount } from "svelte";
	import TodoItem from './TodoItem.svelte';
	let todos = [];
	let newTodo = "";
  
	function addTodo() {
	  if (newTodo.trim() !== "") {
		todos = [...todos, { text: newTodo, completed: false }];
		newTodo = "";
	  }
	}
  
	function toggleTodo(index) {
	  todos = todos.map((todo, i) => i === index ? { ...todo, completed: !todo.completed } : todo);
	}
  
	function deleteTodo(index) {
			todos = todos.filter((task, i) => i !== index);
	}
  </script>
  
  <main>
	<h1>Todo List</h1>
	<input type="text" bind:value={newTodo} placeholder="New todo" />
	<button on:click={addTodo}>Add</button>
	<ul>
	  {#each todos as todo, index}
	  
		<TodoItem {todo} on:toggle={() => toggleTodo(index)} on:delete={() => deleteTodo(index)} />
	  {/each}
	</ul>
  </main>
  
  <style>
	/* Add your styles here */
  </style>
  