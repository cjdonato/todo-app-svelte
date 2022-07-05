<script lang="ts">
  import List from "./List.svelte";

  let task: string = "";

  let taskList: {
    id: number;
    taskName: string;
  }[] = [
    { id: 0, taskName: "Do Svelte" },
    { id: 1, taskName: "Do Express" },
    { id: 2, taskName: "Do Sqlite" },
  ];

  const addTask = () => {
    if (task === "") return;
    taskList = [...taskList, { id: taskList.length, taskName: task }];
    task = "";
  };
</script>

<input id="taskInput" bind:value={task} placeholder="Add a task" />
<button htmlfor="taskInput" on:click={addTask}>Add Task</button>

<List {taskList} />

<style>
</style>
