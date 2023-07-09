<!-- InputCard.svelte -->
<script>
  export let data;
  export let data2;
  export let isOpen;
  export let handleUpdate;
  export let selectedCard;
  export let update;
  let companyName = "";
  let description = "";

  function addCard() {
    if (selectedCard) {
      const newCard = {
        id: Date.now(),
        companyId: selectedCard.id,
        title: companyName,
        description: description,
      };
      console.log("data2 start");
      data2.push(newCard);
      console.log(data2);
      update();
    } else {
      const newCard = {
        id: Date.now(),
        title: companyName,
        description: description,
      };
      console.log("data1 start");
      data.push(newCard);
    }

    handleUpdate();

    companyName = ""; // Reset the input field
    description = ""; // Reset the textarea field
  }
</script>

<div class="form-group {isOpen ? 'w-0 opacity-0' : 'w-full opacity-100'}">
  <input
    class="input"
    type="text"
    required
    placeholder="Company Name"
    bind:value={companyName}
  />
  <textarea placeholder="Description" required bind:value={description} />

  <button
    class=" btn text-purple-700 hover:text-white border border-purple-700 hover:bg-purple-800 focus:ring-4 focus:outline-none focus:ring-purple-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center mr-2 mb-2 dark:border-purple-400 dark:text-purple-400 dark:hover:text-white dark:hover:bg-purple-500 dark:focus:ring-purple-900"
    on:click={addCard}
    disabled={companyName === "" || description === ""}
  >
    SUBMIT
  </button>
</div>

<style>
  .form-group {
    text-align: center;
    margin: 10px 0;
    border: 2px solid white;
    padding: 10px;

    color: black;
  }

  .btn {
    cursor: pointer;
  }
  .input,
  textarea {
    text-align: center;
    padding: 10px;
    margin: 10px 0;
    width: 100%;
  }
</style>
