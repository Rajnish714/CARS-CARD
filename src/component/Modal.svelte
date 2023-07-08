<script>
  import { createEventDispatcher } from "svelte";
  import InputCard from "./InputCard.svelte";
  export let handleUpdate;
  export let cards;
  export let isOpen = false;
  export let isOpened = false;
</script>

{#if isOpened}
  <InputCard data={cards} {handleUpdate} {isOpen} />
{/if}
