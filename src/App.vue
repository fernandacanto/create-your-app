<template>
  <div id="app" class="container"> 
    <div class="row justify-content-md-center mt-lg-5">
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
@import url('https://fonts.googleapis.com/css?family=Roboto');

html, body {
  font-family: 'Roboto', sans-serif;
}

.form-control-file.is-invalid {
	border: 1px solid #dc3545;
	border-radius: 0.25rem;
}
</style>

