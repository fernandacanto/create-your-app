<template>
<div class="col col-lg-10 border container-bg">
  <div class="row p-5">
    <div class="col-lg-7 border-right pl-2 pr-5">
        <Form @obj-change="objChanged"></Form>
    </div>
    <div class="col-lg-5 pl-5 mt-5">
        <Preview :preview="objPreview"></Preview>
        <div class="row justify-content-md-center">
          <a href="#" class="btn btn-primary mt-3">SAVE APP</a>
        </div>
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
  },
  data: function() {
    return {
      objPreview: undefined
    }    
  },
  methods: {
    objChanged(e) {      
      this.objPreview = e;
    }
  }
}
</script>

<style>
.container-bg {
  background: #f2f2f2;
}
</style>