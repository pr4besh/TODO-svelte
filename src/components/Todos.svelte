<script>
   import Todo from "./Todo.svelte";
   export let todos;
</script>

<!-- List of actual todos -->
<div class="app-body">
   <ul>
      {#each todos as todo}
         <Todo
            itemId={todo.id}
            itemText={todo.text}
            completed={todo.completed}
            on:completed
            on:deleted
         />
      {/each}
   </ul>
</div>

<style>
   ul {
      list-style-type: none;
      -webkit-padding-start: 0;
      padding-left: 0px;
   }

   .app-body {
      flex-grow: 1;
      max-height: 600px;
      overflow-x: hidden;
   }
</style>
