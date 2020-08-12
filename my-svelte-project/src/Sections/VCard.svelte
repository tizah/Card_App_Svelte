<script>
  // your script goes here
  export let QRCode = false;
</script>

<style>
  /* your styles go here */
  section {
    width: 400px;
    margin: auto;
    height: 200px;
    color: #fff;
    padding: 30px;
    border-radius: 10px;

    background: rgb(2, 0, 36);
    background: linear-gradient(
      90deg,
      rgba(2, 0, 36, 1) 3%,
      rgba(9, 100, 121, 0.9839286056219363) 68%,
      rgba(0, 212, 255, 1) 100%
    );
  }
</style>

<section>{QRCode}</section>
