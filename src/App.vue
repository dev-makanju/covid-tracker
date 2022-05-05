<template>
  <nav>
      <Header/>
  </nav>
  <div class="wrapper">
      <router-view/>
  </div>
</template>

<script>
import Header from './components/Header.vue'

export default{
    name:'baseApp',
    components:{
      Header,
    }
}

</script>

<style lang="css" scoped>
   .wrapper{
      background-image: url('https://cdn.pixabay.com/photo/2020/03/16/16/29/virus-4937553_960_720.jpg');
      height: 100vh;
      background-repeat:  no-repeat;
      background-size: cover;
   }
</style>

