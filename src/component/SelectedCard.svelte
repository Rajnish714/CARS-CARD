<script>
  export let selectedCard;
  export let expandContent;
  export let nestedData;
  export let isExpanded;
  export let data2;
  export let handleUpdate;

  let form = false;
  import InputCard from "./InputCard.svelte";
  import Modal from "./Modal.svelte";

  function handleNewCard(e) {
    form = !form;
  }

  function update() {
    nestedData;
  }
</script>

<div class="carcard m-10">
  {#if selectedCard}
    <div class="btn">
      <h2 class="  flex items-center justify-center text-2xl font-bold mb-4">
        {selectedCard.title} Nested Data
      </h2>
      <div class="flex items-center justify-center">
        <button
          class=" bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded"
          on:click={expandContent}>Expand</button
        >

        <button
          on:click={() => {
            handleNewCard(selectedCard);
          }}
          class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded"
        >
          {#if !form}
            Add
          {:else}
            Close
          {/if}
        </button>
        {#if form}
          <div class="form flex">
            <InputCard {selectedCard} {data2} {handleUpdate} {update} />
          </div>
        {/if}
      </div>

      <div class="  grid grid-cols-4 gap-4">
        {#if isExpanded}
          {#each nestedData as item}
            <div
              class="  card rounded-lg bg-white p-6 shadow-[0_2px_15px_-3px_rgba(0,0,0,0.07),0_10px_20px_-2px_rgba(0,0,0,0.04)] dark:bg-neutral-700"
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
  {:else}
    <div>
      <h2 class="  flex items-center justify-center text-2xl font-bold mb-4">
        SELECT A CARD FROM SIDE BAR
      </h2>
    </div>
  {/if}
</div>

<style>
  .flex {
    margin: 10px;
  }
  .carcard {
    width: 100%;
    margin: 10px;
    padding: 20px;
    cursor: pointer;
    caret-color: transparent;
  }
  .card:hover {
    box-shadow: 5px 2px 4px rgba(0, 0, 0, 0.9);
  }
  .form {
    justify-content: center;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
    display: flexbox;

    margin: 40px 50px;

    border-radius: 20px;
    padding: 30px;

    background-color: white;
  }
  .form:hover {
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.5);
  }
</style>
