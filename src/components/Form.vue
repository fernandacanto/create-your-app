<template>  
	<form>
		<h1>Create Your App</h1>
		<div class="form-group">
			<label for="appName">APP NAME</label>
			<input type="text" class="form-control" id="appName" placeholder="Enter App display name" 
					v-model="obj.properties.name.value"
					v-bind:class="{ 'is-invalid': !obj.properties.name.isValid && submitted && !obj.properties.name.value }">
		</div>        
		<div class="form-group">
			<label for="appIcon">APP ICON</label>
			<input type="file" class="form-control-file" id="appIcon" placeholder="Drag as image here to update" accept="image/*" 
					@change="imgSelected" 
					v-bind:class="{ 'is-invalid': !obj.properties.icon.isValid && submitted && !obj.properties.icon.value }">
		</div>                

		<div class="form-group">
			<label for="colorIcon">ICON'S BACKGROUND COLORS</label>
			<ColorPicker @color="colorChange" :validation="!obj.properties.color.isValid && submitted && !obj.properties.color.value"></ColorPicker>			
		</div>
		<div class="form-group">
			<label for="appCategory">CATEGORY</label>
			<select class="custom-select" required id="appCategory" 
					v-model="obj.properties.category.value"
					v-bind:class="{ 'is-invalid': !obj.properties.category.isValid && submitted && !obj.properties.category.value }">
				<option disabled>Select a Category</option>
				<option v-for="option in categories" v-bind:key="option.id" v-bind:value="option">
					{{option.name}}
				</option>
			</select>    			
		</div>          

		<div class="alert alert-danger mt-3" role="alert" v-if="submitted">
      All fields must be filled. Please check!
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
	props: {
		preview: Object,
		submitted: Boolean
	},		
	data: function() {
		return {			
			categories: [
				{id: 1, name: "Game"},
				{id: 2, name: "Store"}
			],
			obj: require('@/schema/json-app')
		}
	},
	watch: { 
		obj(e) {
			this.$emit('obj-change', e);
		},
		preview(e) {
			this.obj = e;
		},
		submitted(e) {
			this.submitted = e;
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
				this.obj.properties.icon.value = e.target.result;
				this.$emit('obj-change', this.obj);
			};
			reader.readAsDataURL(file);                     
		},
		colorChange(e) {
			this.obj.properties.color.value = e;
			this.$emit('obj-change', this.obj);
		}
	}
}
</script>

<style>
</style>