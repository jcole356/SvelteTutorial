<script lang="ts">
  import Tag from './Tag.svelte';
  let tags = [
    { name: 'Patrice', value: 1 },
    { name: 'Brad', value: 2 },
  ];
</script>

<style>
  .container {
    border: 1px solid black;
    color: white;
    display: flex;
    flex-wrap: wrap;
    font-size: 48px;
    height: 200px;
    padding: 10px;
  }
</style>

<div class="container">
  {#each tags as tag}
    <Tag name={tag.name} />
  {/each}
</div>
