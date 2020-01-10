<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();

  export let name;
  export let points;
  let showControls = false;

  const plusPoint = () => (points += 1);
  const minusPoint = () => (points -= 1);
  const toggleControls = () => (showControls = !showControls);
  const onDelete = () => dispatch("removeplayer", name);
</script>

<style>
  h1 {
    color: #204f6e;
  }
  h3 {
    margin-bottom: 10px;
  }
</style>

<div class="container">
  <div class="card">
    <h1>
      {name}
      <button class="btn btn-sm" on:click={toggleControls}>
        {#if showControls}close{:else}score{/if}
      </button>
      <button class="btn btn-sm btn-danger" on:click={onDelete}>delete</button>
    </h1>
    {#if showControls}
      <h3>{points}</h3>
      <button class="btn" on:click={plusPoint}>+</button>
      <button class="btn btn-dark" on:click={minusPoint}>-</button>
      <input type="number" bind:value={points} />
    {/if}
  </div>
</div>
