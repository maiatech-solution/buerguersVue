<template>
  <Navbar :logo="logo_src" :alt="app_name"/>
  <router-view/>
  <Footer />
</template>

<script>
  import Navbar from './components/Navbar.vue'
  import Footer from './components/Footer.vue'

  export default{
    components: {
      Navbar,
      Footer
    },
    data(){
      return{
        logo_src: '/img/logo.png',
        app_name: 'Burguers'
      }
    }
  }
</script>

<style>
  * {
    font-family: Helvetica;
    padding: 0;
    margin: 0;
    box-sizing: border-box;
  }

  body{
    background-color: #335;
  }

  h1{
    text-align: center;
    font-size: 42px;
    margin-block: 30px;
    color: #222;
  }


</style>
