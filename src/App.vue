<template>
  <Navbar :logo="logo_src" :alt="app_name" />
  <router-view :alt="app_name"/>
  <Footer :alt="app_name" />
</template>
<script>
import Navbar from './components/Navbar'
import Footer from './components/Footer'

export default {
  components: {
    Navbar,
    Footer
  },
  data() {
    return{
      logo_src: "/img/logo.png",
      app_name: "Mak ya burgah"
    }
  }
}
</script>

<style>
* {
  font-family: Arial, Helvetica, sans-serif;
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
.main-container {
  width: 100%;
  min-height: calc(100vh - 380px);
      box-sizing: border-box;
}
h1 {
  text-align: center;
  font-size: 42px;
  margin-bottom: 30px;
  color: #222;
}
</style>
