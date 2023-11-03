<template>
  <div>
    <AppNavbar />
    <AppConvert/>
  </div>
</template>

<script>
import AppConvert from './components/AppConvert.vue';
import AppNavbar from './components/AppNavbar.vue';



export default {
  name: 'App',
  components: {
    AppNavbar,
    AppConvert,
},
};

</script>

<style>
  
</style>
