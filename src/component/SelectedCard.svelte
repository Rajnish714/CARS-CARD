<script>
  export let selectedCard;
  export let expandContent;
  export let nestedData;
  export let isExpanded;
</script>

<div class="carcard m-10">
  {#if selectedCard}
    <div>
      <h2 class="  flex items-center justify-center text-2xl font-bold mb-4">
        {selectedCard.title} Nested Data
      </h2>
      <div class="flex items-center justify-center">
        <button
          class=" bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded"
          on:click={expandContent}>Expand</button
        >
        <button
          class=" bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded"
          >ADD</button
        >
      </div>

      <div class="m-5 grid grid-cols-4 gap-4">
        <!-- <div class="grid grid-cols-4 gap-4"> -->

        {#if isExpanded}
          {#each nestedData as item}
            <div
              class="  rounded-lg bg-white p-6 shadow-[0_2px_15px_-3px_rgba(0,0,0,0.07),0_10px_20px_-2px_rgba(0,0,0,0.04)] dark:bg-neutral-700"
            >
              <h5
                class="mb-2 text-xl font-medium leading-tight text-neutral-800 dark:text-neutral-50"
              >
                {item.title}
              </h5>
              <p class="mb-4 text-base text-neutral-600 dark:text-neutral-200">
                {item.description}
              </p>
            </div>
          {/each}
        {/if}
      </div>
    </div>
  {/if}
</div>

<style>
  .carcard {
    width: 100%;
  }
</style>
