<script>
  import Modal from "./Modal.svelte";
  export let searchQuery;

  // export let search;
  export let isOpen;
  export let toggleModal;
  export let cards;
  export let cardss;
  export let handleUpdate;
  export let isOpened;
  export let selectedCard;
  export let nestedData;
  export let searchedcard;

  function search() {
    selectedCard = cards.find(
      (card) => card.title.toLowerCase() === searchQuery.toLowerCase()
    );

    nestedData = cardss.filter((card) => card.companyId === selectedCard.id);
    searchedcard(selectedCard, nestedData);
  }
</script>

<div class="p-2">
  <div class="mb-3 {isOpen ? 'w-0 opacity-0' : 'w-full opacity-100'}">
    <div class="relative mb-4 flex w-full flex-wrap items-stretch">
      <input
        type="search"
        class="input relative m-0 -mr-0.5 block w-[1px] min-w-0 flex-auto rounded-l border border-solid-2px border-neutral-300 bg-clip-padding px-3 py-[0.25rem] text-base font-bold leading-[1.6] text-white outline-none transition duration-200 ease-in-out focus:z-[3] focus:border-primary focus:text-neutral-700 focus:shadow-[inset_0_0_0_1px_rgb(59,113,202)] focus:outline-none dark:border-neutral-600 dark:text-neutral-200 dark:placeholder:text-neutral-200 dark:focus:border-primary"
        bind:value={searchQuery}
        placeholder="Search"
        aria-label="Search"
        aria-describedby="button-addon1"
        on:input={() => {}}
      />

      <!--Search button-->
      <button
        class="relative z-[2] flex items-center rounded-r bg-primary px-6 py-2.5 text-xs font-medium uppercase leading-tight text-white shadow-md transition duration-150 ease-in-out hover:bg-primary-700 hover:shadow-lg focus:bg-primary-700 focus:shadow-lg focus:outline-none focus:ring-0 active:bg-primary-800 active:shadow-lg"
        type="button"
        id="button-addon1"
        data-te-ripple-init
        data-te-ripple-color="light"
        on:click={search}
      >
        <svg
          xmlns="http://www.w3.org/2000/svg"
          viewBox="0 0 20 20"
          fill="currentColor"
          class="h-5 w-5"
        >
          <path
            fill-rule="evenodd"
            d="M9 3.5a5.5 5.5 0 100 11 5.5 5.5 0 000-11zM2 9a7 7 0 1112.452 4.391l3.328 3.329a.75.75 0 11-1.06 1.06l-3.329-3.328A7 7 0 012 9z"
            clip-rule="evenodd"
          />
        </svg>
      </button>
    </div>
  </div>
  <button
    class="btn w-full mt-2 p-2 bg-blue-500 hover:bg-blue-700 text-white rounded{isOpen
      ? 'w-0 opacity-0'
      : 'w-full opacity-100'}"
    on:click={toggleModal}
  >
    <!-- <svg xmlns="http://www.w3.org/2000/svg" height="1em" viewBox="0 0 448 512">
      <style>
        svg {
          fill: #ffffff;
        }
      </style><path
        d="M256 80c0-17.7-14.3-32-32-32s-32 14.3-32 32V224H48c-17.7 0-32 14.3-32 32s14.3 32 32 32H192V432c0 17.7 14.3 32 32 32s32-14.3 32-32V288H400c17.7 0 32-14.3 32-32s-14.3-32-32-32H256V80z"
      /></svg
    > -->
    ADD A NEW CARD
  </button>
  <Modal {isOpened} {isOpen} {cards} {handleUpdate} />
</div>

<style>
  .input {
    color: black;
  }

  input::placeholder {
    color: black;
  }
  button {
    font-weight: 1000;
    text-align: center;
    justify-content: center;
  }
</style>
