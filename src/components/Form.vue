<template>  
    <form>
        <h1>Create Your App</h1>
        <div class="form-group">
            <label for="appName">APP NAME</label>
            <input type="text" class="form-control" id="appName" placeholder="Enter App display name">
        </div>        
        <div class="form-group">
            <label for="appIcon">APP ICON</label>
            <input type="file" class="form-control-file" id="appIcon" placeholder="Drag as image here to update">
        </div>                
        <div class="form-group">
            <label for="colorIcon">ICON'S BACKGROUND COLORS</label>
            <ColorPicker></ColorPicker>            
        </div>
        <div class="form-group">
            <label for="appCategory">CATEGORY</label>
            <select class="custom-select" required>
                <option value="">Select a Category</option>
                <option value="1">Um</option>
                <option value="2">Dois</option>
                <option value="3">Três</option>
            </select>
            <div class="invalid-feedback">Exemplo de feedback invalido para o select</div>            
        </div>          
    </form>    
</template>

<script>
import ColorPicker from '../components/ColorPicker.vue'

export default {
    name: 'Form',
    components: {
        ColorPicker
    }
}
</script>

<style>
</style>