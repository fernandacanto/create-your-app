<template>
  <div>
    <p>APP'S CARD REVIEW</p>

    <div class="card">    
      <div class="row no-gutters">
        <div class="col-md-12 col-5 p-0">
          <div class="rectangle" :style="{background: objPreview.properties.color.value}">
            <div class="circle">
              <img class="card-img-top" :src="objPreview.properties.icon.value">
            </div>
          </div>  
        </div>  
        <div class="col-md-12 col-7 p-0">
          <div class="card-body">
            <h5 class="card-title">
              <span v-if="objPreview.properties.name.value">{{objPreview.properties.name.value}}</span>
              <span v-else>App Name</span>
            </h5>
            <p class="card-text">
              <span v-if="objPreview.properties.category.value">{{objPreview.properties.category.value.name}}</span>
              <span v-else>App Category</span>
            </p>            
          </div>        
        </div>        
      </div>        
     </div>     

  </div>
</template>

<script>
export default {
    name: 'Preview',
    props: {
      preview: Object
    },
    data() {
      return {
        objPreview: require('@/schema/json-app')
      }
    },
    watch: {
      preview(e) {
        this.objPreview = e;
      }
    }
}
</script>

<style>
.rectangle {
  width: 100%;
  text-align: center;
  background: #6c757d;
  padding: 5px;
}

.circle {
  background-color: #fff;
  border-radius: 50%;
  width: 150px;
  height: 150px;
  overflow: hidden;
  position: relative;
  margin: 0 auto;
}

.circle img {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
}

@media (max-width: 992px) {
  .circle {
    width: 100px;
    height: 100px;
  }
}
</style>