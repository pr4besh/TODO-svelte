<script>
   import Header from "./components/Header.svelte";
   import Form from "./components/Form.svelte";
   import Todos from "./components/Todos.svelte";

   let newTask;
   let todos = [
      { id: 1, text: "First", completed: false },
      { id: 2, text: "Second", completed: true },
      { id: 3, text: "Third", completed: true },
   ];
   let totalTodos;
   let remainingTodos;

   $: totalTodos = todos.length;
   $: remainingTodos = todos.reduce((n, todo) => {
      return n + (todo.completed ? 0 : 1);
   }, 0);

   function onComplete(event) {
      let updatedID = event.detail.id;
      todos.map((todo) => {
         if (todo.id == updatedID) todo.completed = !todo.completed;
      });
      todos = todos;
   }

   function createdTodo() {
      newTask = newTask.trim();
      if (newTask != "") {
         let newId = Math.max(...todos.map((e) => e.id)) + 1;
         todos = [...todos, { id: newId, text: newTask, completed: false }];
      }
      newTask = "";
   }

   function onDelete(event) {
      let delId = event.detail.id;
      todos = todos.filter((todo) => {
         return todo.id != delId;
      });
   }
</script>

<div id="app-container" class="app-container">
   <Header {totalTodos} {remainingTodos} />
   <Todos {todos} on:completed={onComplete} on:deleted={onDelete} />
   <Form bind:newTask on:created={createdTodo} />
</div>

<style>
   .app-container {
      width: 400px;
      min-height: 500px;
      background-color: #282c34;
      box-shadow: 0 20px 80px rgba(0, 0, 0, 0.6);
      background: radial-gradient(circle, #282c34 0%, rgba(40, 48, 56, 1) 100%);
      position: relative;
      border-radius: 1em;
      padding: 20px;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
   }
</style>
