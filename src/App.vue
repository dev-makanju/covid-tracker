<template>
  <nav>
      <Header/>
  </nav>
  <router-view/>
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

