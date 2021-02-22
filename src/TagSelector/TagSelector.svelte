<script lang="ts">
  import Tag from './Tag.svelte';

  interface Tag {
    name: string;
    value: number;
  }

  let tags: Tag[] = [
    { name: 'Patrice', value: 1 },
    { name: 'Brad', value: 2 },
  ];

  let selectedTags: Tag[] = [];

  function handleSelect(e: Event) {
    const target = e?.target as HTMLInputElement;
    const val = target.value;
    if (val) {
      const tag = tags.find((tag) => (
        tag.value === parseInt(val, 10)
      ));
      if (!tag) {
        return;
      }
      if (selectedTags.indexOf(tag) < 0) {
        const newTags = [...selectedTags, tag];
        selectedTags = newTags;
      }
    }
  }
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
  {#each selectedTags as tag}
    <Tag name={tag.name} />
  {/each}
</div>
<select on:change={handleSelect}>
  <option selected value="">Select a Bruin</option>
  {#each tags as tag}
    <option value={tag.value}>{tag.name}</option>
  {/each}
</select>
