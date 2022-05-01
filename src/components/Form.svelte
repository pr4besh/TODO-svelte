<script>
   import { createEventDispatcher } from "svelte";
   const dispatch = createEventDispatcher();

   export let newTask;

   function created() {
      dispatch("created");
   }
</script>

<!-- Add form at bottom -->
<div class="app-form">
   <input
      bind:value={newTask}
      placeholder="Add Task"
      type="text"
      class="input-text"
      name=""
   />
   <button class="btn fa-solid fa-plus" on:click={created} />
</div>

<style>
   .app-form {
      margin-bottom: 10px;
      display: flex;
      justify-content: center;
   }

   .input-text {
      height: 40px;
      background: #282c34;
      font-size: 15px;
      border: 1px solid aqua;
      color: aqua;
      width: 100%;
      margin-right: 15px;
      border-radius: 1.5em;
      padding: 10px;
      transition: border 250ms ease-out;
   }

   .input-text:focus {
      background: #1d2025;
      outline: none;
      color: #dce4ec;
   }

   .btn {
      color: aqua;
      cursor: pointer;
      font-size: 15px;
      padding: 10px 12px;
      border-radius: 2em;
      background: none;
      border: 0px solid;
      transition: 250ms ease-out;
   }

   .btn:hover {
      color: white;
   }

   .btn:focus {
      outline: none;
   }

   ::placeholder {
      opacity: 0.3;
   }
</style>
