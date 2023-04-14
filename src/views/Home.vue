<template>
  <Banner />
  <div class="main-container">
    <h1>Monte seu Burguer</h1>
  </div>
  <BurguersForm />
</template>
  
<script>
  import Banner from "../components/Banner.vue";
  import BurguersForm from "../components/BurguersForm.vue";
  export default {
    name: "Home",
    components: {
      Banner,
      BurguersForm
    },
  };
</script>

<style scoped>
  .main-container h1{
    color: #dddddd;
  }
</style>