<script>
  export let cards;
  export let ClickedCard;
  export let isOpen;
</script>

<div class="container mx-auto">
  {#each cards as card}
    <button
      class="  card w-full max-w-sm mx-auto my-2 shadow-md rounded-lg overflow-hidden {isOpen
        ? 'w-0 opacity-0'
        : 'w-full opacity-100'}"
      on:click={() => ClickedCard(card)}
    >
      <div class="px-6 py-4 text-black">
        <h3 class="text-white font-semibold">{card.title}</h3>
      </div>
      <div class="px-6 py-4">
        <p class="text-white-700">{card.description}</p>
      </div>
    </button>
  {/each}
</div>

<style>
  .container {
    padding: 10px;
  }
  .card {
    box-shadow: 0px 0px 1px 2px rgba(211, 209, 209, 0.9);
  }
  .card:hover {
    box-shadow: 0px 0px 4px 5px rgba(211, 209, 209, 0.9);
  }
</style>
