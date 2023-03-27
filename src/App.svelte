<script>
  var tasks = [ {task:'workout', state:false},
               {task:'homework', state:false},
               {task:'reading', state:false}
  ];

  var newTask = '';
  
  function addTask(){
    if(newTask == ''){
      alert('please add your task');
      return ;
    }
    tasks = [ ...tasks, {task:newTask, state:false}];
    newTask = '';
  }

  function removeTask(index){
    tasks.splice(index, 1);
    tasks = tasks;
  }
  
</script>

<main>
  <input bind:value={newTask} type="text" placeholder="add task">
  <button on:click={addTask}>ADD</button>
  <br>
  
  {#each tasks as item, index}
    <input bind:checked={item.state} type="checkbox">
    <span class:done={item.state} >{item.task}</span>
    <span on:click={() => removeTask(index)}>❌</span>
    <br>
  {/each}
</main>

<style>
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }
  .done {
    text-decoration: line-through;
  }
</style>
