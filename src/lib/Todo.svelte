<script lang="ts">
  import { onMount } from "svelte";
  import axios from "axios";

  import Input from "./Input.svelte";
  import List from "./List.svelte";

  let taskList: {
    id: number;
    name: string;
    isDone: boolean;
  }[] = [];

  onMount(async () => {
    try {
      const res = await axios.get(`http://localhost:3001/todo`);
      taskList = res.data;
    } catch (error) {
      console.log(error);
    }
  });

  const handleSubmit = async (event: CustomEvent<any>) => {
    await addTask(event.detail.text);
  };

  const handleFinish = async (event: CustomEvent<any>) => {
    await finishTask(event.detail.id);
  };

  const handleDelete = async (event: CustomEvent<any>) => {
    await deleteTask(event.detail.id);
  };

  const addTask = async (task: string) => {
    if (task === "") return;

    const res = await axios.post(`http://localhost:3001/todo`, {
      name: task,
    });

    taskList = [...taskList, res.data];
    task = "";
  };

  const finishTask = async (id: number) => {
    const res = await axios.put(`http://localhost:3001/todo`, {
      id,
      isDone: true,
    });

    taskList = taskList.map((task) => (task.id === id ? res.data : task));
  };

  const deleteTask = async (id: number) => {
    const res = await axios.delete(`http://localhost:3001/todo`, {
      data: { id },
    });

    taskList = taskList.filter((task) => task.id !== res.data.id);
  };
</script>

<Input on:submit={handleSubmit} />

<List {taskList} on:finish={handleFinish} on:delete={handleDelete} />

<style>
</style>
