<template>
<div class="col col-lg-10 border">
  <div class="row p-3">
    <div class="col-lg-8 border-right">
        <Form></Form>     
    </div>
    <div class="col-lg-4">
        <Preview></Preview>
    </div>
  </div>
</div>
</template>

<script>
import Form from '../components/Form.vue'
import Preview from '../components/Preview.vue'

export default {
  name: 'Container',
  components: {
    Form,
    Preview
  }
}
</script>

<style>
</style>