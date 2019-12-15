<template>
<div class="col col-lg-10 border container-bg">  
  <div class="row p-5">
    <div class="col-lg-7 border-right pl-lg-2 pr-lg-5">
       <Form @obj-change="objChanged" :preview="objPreview" :submitted="submitted"></Form>
    </div>
    <div class="col-lg-5 pl-lg-5 mt-5">
      <Preview :preview="objPreview"></Preview>
      
      <div class="row justify-content-center">
        <a href="#" class="btn mt-3 btn-secondary" v-on:click="submit()">SAVE APP</a>
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
      objPreview: require('@/schema/json-app'),
      submitted: false
    }    
  },
  methods: {
    objChanged(e) {      
      this.objPreview = e;      
    }, 
    validate() {
      let properties = this.objPreview.properties;
      let isInvalid = false;

      for (const key in properties) {
        if (properties.hasOwnProperty(key)) {
          const element = properties[key];     
          if (element.value) {
            element.isValid = true;          
          } else {
             isInvalid = true; 
          }          
        }
      }

      return isInvalid;
    },
    submit() { 
      this.submitted = true;
      if (this.validate()) {        
        return;
      }
      /* eslint-disable */
      console.log(this.objPreview);
      alert("App created correctly!");
    }
  }
}
</script>

<style>
.container-bg {
  background: #f2f2f2;
}
</style>