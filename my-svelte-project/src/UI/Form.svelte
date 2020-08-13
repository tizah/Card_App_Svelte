<script>
  import { createEventDispatcher } from "svelte";

  export let values = {
    name: "",
    organizaion: "",
    jobTitle: "",
    phoneNumber: "",
    address: "",
    email: "",
    photoURL: "https://i.pravatar.cc/100?img=68",
    logoURL: "https://icongr.am/entypo/database.svg?size=40&color=3d9afd",
    backgroundURL:
      "https://images.unsplash.com/photo-1523961131990-5ea7c61b2107?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1267&q=80",
  };

  let disabled = true;
  let name = "";
  let firstInput = "";
  let active = {
    name: false,
    organizaion: fasle,
    jobTitle: false,
    phoneNumber: false,
    address: false,
    email: false,
    photoURL: false,
    logoURL: false,
    background: false,
  };

  const inputData = {
    name: {
      lable: "Name",
      type: "text",
      placeholder: "Your Contact Name",
    },
    organization: {
      lable: "Organization",
      type: "text",
      placeholder: "Enter your Orgganization",
    },
    jobTitle: {
      lable: "Jot Title",
      type: "text",
      placeholder: "What is your Job Title",
    },
    phone: {
      lable: "Phone",
      type: "text",
      placeholder: "Enter your Mobile Number",
    },
    address: {
      lable: "Address",
      type: "text",
      placeholder: "Enter your address",
    },
    email: {
      lable: "Email",
      type: "text",
      placeholder: "Enter your Email address ",
    },
    photoURl: {
      lable: "Phote Url",
      type: "text",
      placeholder: "Url for your Photo",
    },
    logoURL: {
      lable: "Logo Url",
      type: "text",
      placeholder: "Url for your company Logo",
    },
    backgroundURL: {
      lable: "Background Url",
      type: "text",
      placeholder: "Url for your background Url",
    },
  };

  const dispatch = createEventDispatcher();
  function keyPressed(event) {
    console.log(event);

    event.key === "Shift" ? "" : (disabled = false);
  }

  function resetForm() {
    values = { ...values, photoURL: "", logoURL: "", backgroundURL: "" };
    disabled = true;
    firstInput.focus();
  }
</script>

<style>
  label {
    display: flex;
    align-items: baseline;
    margin: 0.5rem;
    font-weight: bold;
  }
  input {
    width: 70%;
    margin: 0 0.5rem;
    border-radius: 5px;
  }
  article {
    display: flex;
    justify-content: space-evenly;
  }
  button {
    margin: 0.5rem 0;
    cursor: pointer;
    border-radius: 5px;
  }
  .labelText {
    text-align: end;
    width: 30%;
  }
  .active {
    border-color: hsl(211, 63%, 35%);
    box-shadow: 0 1px 3px hsla(211, 63%, 35%, 0.4);
  }
</style>

<form>
  <label>
    <div class="labelText">{inputData.name.lable}</div>

    <input
      type="text"
      placeholder={inputData.name.placeholder}
      class:active={active.name}
      on:focus={() => {
        active.name = true;
      }}
      on:blue={() => {
        active.name = false;
      }}
      on:keydown={keyPressed}
      bind:value={values.name}
      bind:this={firstInput} />
  </label>

  <label>
    <div class="lableText">{inputData.organization.lable}</div>

    <input
      type="text"
      placeholder={inputData.organization.placeholder}
      class:active={active.organization}
      on:focus={() => {
        active.organization = true;
      }}
      on:blue={() => {
        active.organization = false;
      }}
      on:keydown={keyPressed}
      bind:value={values.organization}
      bind:this={firstInput} />
  </label>

  <label>
    <div class="labelText">{inputData.jobTitle.lable}</div>

    <input
      type="text"
      placeholder={inputData.jobTitle.placeholder}
      class:active={active.jobTitle}
      on:focus={() => {
        active.jobTitle = true;
      }}
      on:blue={() => {
        active.jobTitle = false;
      }}
      on:keydown={keyPressed}
      bind:value={values.jobTitle}
      bind:this={firstInput} />
  </label>

  <lable>
    <div class="labelText">{inputData.phone.lable}</div>
    <input
      type="text"
      placeholder={inputData.phone.placeholder}
      class:active={active.phone}
      on:focus={() => {
        active.phone = true;
      }}
      on:blue={() => {
        active.phone = false;
      }}
      on:keydown={keyPressed}
      bind:value={values.jobTitle}
      bind:this={firstInput} />
  </lable>

  <label>
    <div class="labelText">{inputData.email.lable}</div>

    <input
      type="text"
      placeholder={inputData.email.placeholder}
      class:active={active.email}
      on:focus={() => {
        active.email = true;
      }}
      on:blue={() => {
        active.email = false;
      }}
      on:keydown={keyPressed}
      bind:value={values.email}
      bind:this={firstInput} />
  </label>

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
