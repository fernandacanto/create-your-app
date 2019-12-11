<template>
  <div class="input-group mb-2 mr-sm-2">
    <input type="text" class="form-control" id="colorIcon" placeholder="Pick a color" v-model="colorHex">
    <div class="input-group-prepend">
      <div class="input-group-text"> #{{colorHex || 'FFFFFF'}} </div>
    </div>
  </div>

    
</template>
<script>
export default {
    name: 'ColorPicker',
    data() {
        return {
            colorHex: ''
        }
    }
}
</script>