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

<input id="taskInput" bind:value={task} placeholder="Task name" class="input input-bordered w-full max-w-xs"/>

<button htmlfor="taskInput" on:click={addTask} class="btn">Add Task</button>

<style>
</style>
