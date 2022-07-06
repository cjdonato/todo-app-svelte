<script lang="ts">
  import { createEventDispatcher } from 'svelte';

  const dispatch = createEventDispatcher();

  let task: string = "";

  const addTask = () => {
    dispatch('submit', {
      text: task
    });
  }
</script>

<input id="taskInput" bind:value={task} placeholder="Task name" />

<button htmlfor="taskInput" on:click={addTask}>Add Task</button>

<style>
</style>
