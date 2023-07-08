<script>
  import Modal from "./Modal.svelte";
  export let searchQuery;
  export let search;
  export let isOpen;
  export let toggleModal;
  export let cards;
  export let handleUpdate;
  export let isOpened;
</script>

<div class="p-2">
  <input
    type="text"
    class="w-full mb-2 p-2 border border-gray-300 rounded {isOpen
      ? 'w-0 opacity-0'
      : 'w-full opacity-100'}"
    bind:value={searchQuery}
    placeholder="Search"
    on:input={() => {}}
  />

  <button
    class="w-full p-2 bg-blue-500 text-white rounded {isOpen
      ? 'w-0 opacity-0'
      : 'w-full opacity-100'}"
    on:click={search}
  >
    Search
  </button>

  <button
    class="w-full mt-2 p-2 bg-blue-500 text-white rounded{isOpen
      ? 'w-0 opacity-0'
      : 'w-full opacity-100'}"
    on:click={toggleModal}
  >
    ADD
  </button>
  <Modal {isOpened} {isOpen} {cards} {handleUpdate} />
</div>

<style>
  input {
    color: black;
  }
</style>
