<script>
  import Navbar from "./Sections/Navbar.svelte";
  import Form from "./UI/Form.svelte";
  import VCard from "./Sections/VCard.svelte";
  import Footer from "./Sections/Footer.svelte";
  import { loop_guard } from "svelte/internal";

  let QRCode = "";
  let values;
  let print;
</script>

<style>
  main {
    display: flex;
    margin: 0 auto;
    max-width: 90%;
    padding: 1rem;
  }
</style>

<Navbar title="E-Card Generator" />
<main>
  <Form
    bind:values
    bind:print
    on:Print={(e) => {
      console.log({ e });
      print = e.detail.print;
    }}
    on:CreateCode={(e) => {
      QRCode = e.detail;
    }} />

  <VCard {values} {QRCode} {print} />

</main>

<Footer {QRCode} />
