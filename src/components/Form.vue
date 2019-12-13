<template>  
	<form>
		<h1>Create Your App</h1>
		<div class="form-group">
			<label for="appName">APP NAME</label>
			<input type="text" class="form-control" id="appName" placeholder="Enter App display name" v-model="obj.name">
		</div>        
		<div class="form-group">
			<label for="appIcon">APP ICON</label>
			<input type="file" class="form-control-file" id="appIcon" placeholder="Drag as image here to update" @change="imgSelected">
		</div>                
		<div class="form-group">
			<label for="colorIcon">ICON'S BACKGROUND COLORS</label>
			<ColorPicker @color="colorChange"></ColorPicker>    			
		</div>
		<div class="form-group">
			<label for="appCategory">CATEGORY</label>
			<select class="custom-select" required id="appCategory" v-model="obj.category">
				<option disabled>Select a Category</option>
				<option v-for="option in categories" v-bind:key="option.id" v-bind:value="option">
					{{option.name}}
				</option>
			</select>                  
		</div>          
	</form>    
</template>

<script>
import ColorPicker from '../components/ColorPicker.vue'

export default {
	name: 'Form',
	components: {
		ColorPicker
	},
	data: function() {
		return {
			categories: [
				{id: 1, name: "Game"},
				{id: 2, name: "Store"}
			],
			obj: {}     
		}
	},
	watch: { 
		obj(e) {
			this.$emit('obj-change', e);
		}
	},
	methods: {
		imgSelected(e) {            
			let files = e.target.files || e.dataTransfer.files;
			if (!files.length) { 
				return
			}            
			this.createImage(files[0]);            
		},
		createImage(file) {
			let reader = new FileReader();
			reader.onload = (e) => {
				this.obj.icon = e.target.result;
				this.$emit('obj-change', this.obj);
			};
			reader.readAsDataURL(file);                     
		},
		colorChange(e) {
			this.obj.color = e;
			this.$emit('obj-change', this.obj);
		}
	}
}
</script>

<style>
</style>