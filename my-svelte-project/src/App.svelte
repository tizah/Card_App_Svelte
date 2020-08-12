<script>
  import Navbar from "./Sections/Navbar.svelte";
  import Form from "./UI/Form.svelte";
  import VCard from "./Sections/VCard.svelte";
  import Footer from "./Sections/Footer.svelte";

  let QRCode = "";
</script>

<style>
  main {
    margin: 0 auto;
    max-width: 60%;
    padding: 1rem;
  }
</style>

<Navbar title="vCard Generator" />
<main>
  <Form
    on:CreateCode={(e) => {
      QRCode = e.detail;
    }} />

  <VCard {QRCode} />

</main>

<Footer {QRCode} />
