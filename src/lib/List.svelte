<script lang="ts">
  export let taskList: {
    id: number;
    taskName: string;
  }[];
</script>

<ul>
  {#each taskList as { id, taskName }, i}
    <li>
      {taskName}
    </li>
  {/each}
</ul>

<style>
</style>
