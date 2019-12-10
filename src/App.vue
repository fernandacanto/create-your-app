<template>
  <div id="app" class="container"> 
    <div class="row justify-content-md-center mt-5">
      <Container></Container>
    </div>      
  </div>
</template>

<script>
import Container from './components/Container.vue'

export default {
  name: 'app',
  components: {
    Container
  }
}
</script>

<style>
  @import '../node_modules/bootstrap/dist/css/bootstrap.css';
</style>
