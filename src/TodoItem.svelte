<script>
    import { createEventDispatcher } from 'svelte';
  
    export let todo;
    const dispatch = createEventDispatcher();
  
    function toggle() {
      dispatch('toggle');
    }
  
    function remove() {
      dispatch('delete');
    }
  </script>
  
  <li>
    <input type="checkbox" checked={todo.completed} on:change={toggle} />
    <span style="text-decoration: {todo.completed ? 'line-through' : 'none'}">{todo.text}</span>
    <button on:click={todo.completed ? remove:""}>Delete</button>
  </li>
  
  <style>
    /* Add your styles here */
  </style>
  