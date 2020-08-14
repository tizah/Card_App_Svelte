<script>
  import { createEventDispatcher } from "svelte";

  function printSection() {
    console.log("hey print me");
    // let printDiv = document.getElementById("printDiv").innerHTML;
    // document.body.innerHTML = printDiv;
    // window.print();
  }

  export let values = {
    name: "",
    organization: "",
    jobTitle: "",
    phoneNumber: "",
    address: "",
    email: "",
    photoURL:
      "https://res.cloudinary.com/practicaldev/image/fetch/s--2tRgHd7f--/c_fill,f_auto,fl_progressive,h_320,q_auto,w_320/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/381629/ece96c10-55d1-4853-a0a7-3631e5f41313.jpeg",
    logoURL: "https://icongr.am/entypo/database.svg?size=40&color=3d9afd",
    backgroundURL:
      "https://images.unsplash.com/photo-1523961131990-5ea7c61b2107?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1267&q=80",
  };

  let disabled = true;
  let name = "";
  let firstInput = "";
  let active = {
    name: false,
    organization: false,
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
    phoneNumber: {
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
    dispatch("createQRCode", false);
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
  container {
    display: flex;
    flex-direction: column;
    width: 40%;
  }
</style>

<container>
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
      <div class="labelText">{inputData.organization.lable}</div>

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
        bind:value={values.organization} />
    </label>

    <label>
      <div class="labelText">{inputData.address.lable}</div>
      <input
        type="text"
        placeholder={inputData.address.placeholder}
        class:active={active.address}
        on:focus={() => {
          active.address = true;
        }}
        on:blur={() => {
          active.address = false;
        }}
        on:keydown={keyPressed}
        bind:value={values.address} />
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
        bind:value={values.jobTitle} />
    </label>

    <label>
      <div class="labelText">{inputData.phoneNumber.lable}</div>
      <input
        type="text"
        placeholder={inputData.phoneNumber.placeholder}
        class:active={active.phone}
        on:focus={() => {
          active.phoneNumber = true;
        }}
        on:blue={() => {
          active.phoneNumber = false;
        }}
        on:keydown={keyPressed}
        bind:value={values.phoneNumber} />
    </label>

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
        bind:value={values.email} />
    </label>

    <label>
      <div class="labelText">{inputData.photoURl.lable}</div>

      <input
        type="text"
        placeholder={inputData.photoURl.placeholder}
        class:active={active.photoURl}
        on:focus={() => {
          active.photoURl = true;
        }}
        on:blue={() => {
          active.photoURl = false;
        }}
        on:keydown={keyPressed}
        bind:value={values.photoURL} />
    </label>

    <label>
      <div class="labelText">{inputData.logoURL.lable}</div>

      <input
        type="text"
        placeholder={inputData.logoURL.placeholder}
        class:active={active.logoURL}
        on:focus={() => {
          active.logoURL = true;
        }}
        on:blue={() => {
          active.logoURL = false;
        }}
        on:keydown={keyPressed}
        bind:value={values.logoURL} />
    </label>

    <label>
      <div class="labelText">{inputData.backgroundURL.lable}</div>

      <input
        type="text"
        placeholder={inputData.backgroundURL.placeholder}
        class:active={active.backgroundURL}
        on:focus={() => {
          active.backgroundURL = true;
        }}
        on:blue={() => {
          active.backgroundURL = false;
        }}
        on:keydown={keyPressed}
        bind:value={values.backgroundURL} />
    </label>

  </form>
  <article>
    <buttonContainer>
      <button {disabled} on:click={resetForm}>Reset</button>

      <button
        on:click|preventDefault={(e) => {
          dispatch('CreateCode', true);
        }}>
        Create QRCode
      </button>

      <button on:click|preventDefault={() => alert('coming soon')}>
        Print Card
      </button>

      <button on:click|preventDefault={() => alert('coming soon')}>
        Customize Card
      </button>

    </buttonContainer>
  </article>
</container>
