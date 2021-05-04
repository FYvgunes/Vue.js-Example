<template>
  <div id="app">
    <profilList/>
  </div>
</template>

<script>
import profilList from "./components/ProfilList";
export default {
  name: 'app',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  components:{
    profilList
  }
}
</script>

<style lang="scss">

</style>
