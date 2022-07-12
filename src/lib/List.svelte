<script lang="ts">
  export let taskList: {
    id: number;
    taskName: string;
  }[];
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
      {#each taskList as { id, taskName }, i}
        <tr>
          <td><span class="badge badge-success">Done</span></td>
          <td>{taskName}</td>
          <td>
            <button class="btn btn-sm btn-success">Finish</button>
            <button class="btn btn-sm btn-error">Delete</button>
          </td>
        </tr>
      {/each}
    </tbody>
  </table>
</div>

<style>
</style>
