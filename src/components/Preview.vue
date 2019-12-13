<template>
  <div>
    <p>APP'S CARD REVIEW</p>

    <div class="card">    
      <div class="rectangle" :style="{background: objPreview.color}">
        <div class="circle">
          <img class="card-img-top" :src="objPreview.icon">
        </div>
      </div>  
        <div class="card-body">
            <h5 class="card-title">
              <span v-if="objPreview.name">{{objPreview.name}}</span>
              <span v-else>App Name</span>
            </h5>
            <p class="card-text">
              <span v-if="objPreview.category">{{objPreview.category.name}}</span>
              <span v-else>App Category</span>
            </p>            
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
        objPreview: {}
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
}

.circle {
  background-color: #fff;
  border-radius: 50%;
  width: 150px;
  height: 150px;
  overflow: hidden;
  position: relative;
  margin: 5px auto;
}

.circle img {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;

}
</style>