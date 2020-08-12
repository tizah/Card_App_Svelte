<script>
  import { createEventDispatcher } from "svelte";
  let disabled = true;
  let name = "";
  let firstInput = "";
  let active = false;

  const dispatch = createEventDispatcher();
  function keyPressed(event) {
    console.log(event);

    event.key === "Shift" ? "" : (disabled = false);
  }

  function resetForm() {
    firstInput.focus();
    name = "";
    disabled = true;
  }
</script>

<style>
  input {
    display: flex;
    width: 50%;
    margin: auto;
    border-radius: 5px;
  }
  buttonContainer {
    display: flex;
    justify-content: space-evenly;
  }

  button {
    margin: 0.5rem 0;
    cursor: pointer;
    border-radius: 5px;
  }
  .active {
    border-color: hsl(211, 63%, 35%);
    box-shadow: 0 1px 3px hsla(211, 63%, 35%, 0.4);
  }
</style>

<form>
  <input
    type="text"
    placeholder="Please enter your name"
    class:active
    on:focus={() => {
      active = true;
    }}
    on:blue={() => {
      active = false;
    }}
    on:keydown={keyPressed}
    bind:value={name}
    bind:this={firstInput} />

</form>
<buttonContainer>
  <button {disabled} on:click={resetForm}>Reset</button>

  <button
    on:click|preventDefault={(e) => {
      dispatch('CreateCode', name);
    }}>
    Create QRCode
  </button>

</buttonContainer>
>
