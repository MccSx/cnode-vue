<template>
  <div id="app">
    <Header/>
    <!-- <router-view/> -->
  </div>
</template>

<script>
import Header from './components/Header'

export default {
  name: 'App',
  components: {
    Header
  }
}
</script>

<style>
*{margin: 0; padding: 0; box-sizing: border-box;}
*::after{box-sizing: border-box;}
*::before{box-sizing: border-box;}
li{list-style: none;}
a{text-decoration: none; color: #C7C3C7;}

</style>
