<template>
  <div id="app">
    <!-- <RwvHeader /> -->
    <home></home>
    <!-- <RwvFooter /> -->
  </div>
</template>

<script>
import Home from './views/Home.vue';

//import RwvHeader from "@/components/TheHeader";
//import RwvFooter from "@/components/TheFooter";

export default {
  name: "App",
  components: {
    Home
   // RwvHeader,
   // RwvFooter
  }
};
</script>

<style></style>
