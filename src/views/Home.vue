<template>
  <div class="main-container">
    <Banner :alt="alt"/>
    <h1>Monte seu burguer:</h1>
    <Formburger />
  </div>
</template>

<script>
import Banner from "../components/Banner"
import Formburger from "../components/Formburger"
export default {
  name: "Home",
  props: ["alt"],
  components: {
    Banner,
    Formburger
  }
} 
</script>
