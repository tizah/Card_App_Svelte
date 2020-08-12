<script>
  let disabled = true;
  let name = "";
  let firstInput = "";
  let active = false;

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

  <button {disabled} on:click={resetForm}>Reset</button>
</form>
{name}
