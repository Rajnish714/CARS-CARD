<!-- InputCard -->
<!-- <div class="form-group">
  <input type="text" placeholder="Company Name" />
  <textarea name="text" id="text1" placeholder="Decription" />
</div>

<style>
  .form-group {
    text-align: center;
    margin: 10px 0;
    border: 2px solid white;
    padding: 10px;
    color: black;
  }
  input {
    text-align: center;
    padding: 10px;
    margin: 10px 0;

    width: 100%;
  }
  textarea {
    text-align: center;
    width: 100%;
  }
</style> -->
<!-- InputCard.svelte -->
<!-- InputCard.svelte -->
<!-- <script>
  let companyName = "";
  let description = "";
</script>

<div class="form-group">
  <input
    type="text"
    placeholder="Company Name"
    on:input={(event) => (companyName = event.target.value)}
  />
  <textarea
    placeholder="Description"
    on:input={(event) => (description = event.target.value)}
  />
  <button
    class="cards py-2 px-4 transition-all duration-300"
    on:click={addCard}
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
  .cards {
    border: white 2px solid;
    text-align: center;
    cursor: pointer;
    border-radius: 10px;
  }

  .cards h5 {
    border-bottom: white 2px solid;
    margin: 5px;
    padding: 5px;
  }

  .cards:hover {
    background-color: rgb(4, 68, 121);
  }
  input,
  textarea {
    text-align: center;
    padding: 10px;
    margin: 10px 0;
    width: 100%;
  }
</style> -->
<!-- InputCard.svelte -->
<script>
  import { createEventDispatcher } from "svelte";
  export let data;
  export let isOpen;
  export let handleUpdate;
  let companyName = "";
  let description = "";

  function addCard() {
    const newCard = {
      id: Date.now(),
      title: companyName,
      description: description,
    };

    data.push(newCard);
    handleUpdate();
    // dispatch("cardAdded", newCard); // Emit the custom event with the new card data

    companyName = ""; // Reset the input field
    description = ""; // Reset the textarea field
  }
</script>

<div class="form-group {isOpen ? 'w-0 opacity-0' : 'w-full opacity-100'}">
  <input type="text" placeholder="Company Name" bind:value={companyName} />
  <textarea placeholder="Description" bind:value={description} />
  <button
    class="cards py-2 px-4 transition-all duration-300"
    on:click={addCard}
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
  .cards {
    border: white 2px solid;

    width: fit-content;
    cursor: pointer;
    border-radius: 10px;
  }

  .cards:hover {
    background-color: rgb(4, 68, 121);
  }
  input,
  textarea {
    text-align: center;
    padding: 10px;
    margin: 10px 0;
    width: 100%;
  }
</style>
