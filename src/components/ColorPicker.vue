<template>
  <div class="input-group mb-2 mr-sm-2">
    <input type="color" class="form-control" id="colorIcon" placeholder="Pick a color" v-model="colorHex">
    <div class="input-group-prepend">
      <div class="input-group-text"> {{colorHex}} </div>
    </div>
  </div>

    
</template>
<script>
export default {
    name: 'ColorPicker',
    data() {
        return {
            colorHex: '#6c757d'
        }
    },
    watch: {
      colorHex(e) {
        this.$emit("color", e);
      }
    }
}
</script>