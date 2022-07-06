<script lang="ts">
  import Input from "./Input.svelte";
  import List from "./List.svelte";

  let taskList: {
    id: number;
    taskName: string;
  }[] = [
    { id: 0, taskName: "Do Svelte" },
    { id: 1, taskName: "Do Express" },
    { id: 2, taskName: "Do Sqlite" },
  ];

  const handleSubmit = (event) => {
    addTask(event.detail.text);
  };

  const addTask = (task: string) => {
    if (task === "") return;
    taskList = [...taskList, { id: taskList.length, taskName: task }];
    task = "";
  };
</script>

<Input on:submit={handleSubmit} />

<List {taskList} />

<style>
</style>
