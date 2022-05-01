<script>
   export let totalTodos;
   export let remainingTodos;
</script>

<!-- Header with information -->
<div class="app-header">
   <div class="task">{totalTodos} Tasks</div>
   <div class="task-count">{remainingTodos} Remaining</div>
</div>

<style>
   .task,
   .task-count {
      color: aqua;
      font-weight: bold;
      font-size: 20px;
   }

   .app-header {
      padding: 10px;
      display: flex;
      justify-content: space-between;
   }

   .task-count {
      align-self: center;
   }
</style>
