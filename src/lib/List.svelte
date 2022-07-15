<script lang="ts">
  import { createEventDispatcher } from "svelte";

  export let taskList: {
    id: number;
    name: string;
    isDone: boolean;
  }[];

  const dispatch = createEventDispatcher();

  const finishTask = (id: number) => {
    dispatch("finish", { id });
  };

  const deleteTask = (id: number) => {
    dispatch("delete", { id });
  };
</script>

<div class="overflow-x-auto w-10/12 inline-block mt-10">
  <table class="table w-full">
    <thead>
      <tr>
        <th>Status</th>
        <th class="w-8/12">Name</th>
        <th>Actions</th>
      </tr>
    </thead>
    <tbody>
      {#each taskList as task (task.id)}
        <tr>
          {#if task.isDone}
            <td><span class="badge badge-success">Done</span></td>
          {:else}
            <td><span class="badge badge-warning">Not Done</span></td>
          {/if}
          <td>{task.name}</td>
          <td>
            <button
              class="btn btn-sm btn-success"
              disabled={task.isDone}
              on:click={() => finishTask(task.id)}>Finish</button
            >
            <button
              class="btn btn-sm btn-error"
              on:click={() => deleteTask(task.id)}>Delete</button
            >
          </td>
        </tr>
      {:else}
        <p>...Loading</p>
      {/each}
    </tbody>
  </table>
</div>

<style>
</style>
