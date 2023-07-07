<script>
  import { onMount } from "svelte";
  import { data2 } from "./data";

  export let selectedCard = null;

  let nestedData = [];

  onMount(() => {
    if (selectedCard) {
      nestedData = data2.filter((item) => item.companyId === selectedCard.id);
    }
  });
</script>

<div class="mt-4">
  <h2 class="font-bold text-lg mb-2">
    Nested Data for {selectedCard.title}
  </h2>

  <ul>
    {#each nestedData as item}
      <li class="p-2 border rounded mb-2">
        <h3 class="font-bold">{item.title}</h3>
        <p>{item.description}</p>
      </li>
    {/each}
  </ul>
</div>
