<script>
    let tasks = [];
    let newTask = "";
    let completeTasks = [];

    function handleAddTask() {
        tasks = [...tasks, newTask];
        newTask = "";
    }

    function handleCompleteTask(index, task) {
        completeTasks = [...completeTasks, task];
        tasks.splice(index, 1);
        tasks = tasks
    }

    function handleRemove(index) {
        tasks.splice(index, 1);
        tasks = tasks
    }

    function handleDelete(index) {
        completeTasks.splice(index, 1)
        completeTasks = completeTasks
    }

</script>

<main>
    <div>
        <h3>Todo task manager</h3>
        <div>
            <input bind:value={newTask} />
            <button on:click={handleAddTask}>Add</button>
        </div>
    </div>

    <div>
        <h3>Todo Tasks</h3>
        <ol>
            {#each tasks as task, index}
                <li>
                    {task}
                    <button on:click={()=>handleCompleteTask(index, task)}>complete</button>
                    <button on:click={()=>handleRemove(index)}>remove</button>
                </li>
            {/each}
                
        </ol>
    </div>

    <div>
        <h3>complete tasks</h3>
        <ol>
            {#each completeTasks as completeTask, index }
                <li>
                    {completeTask}
                    <button on:click={()=>handleDelete(index)}>remove</button>
                </li>
                
            {/each}
        </ol>
    </div>

</main>