<template>
  <div class="HOME">
  	<q-card class="bg-white q-mb-md" align="center">
  		<h6>Rich Text Editor Component</h6>
  	</q-card>
  	<div class="row gutter-sm">
  		<div class="col-lg-12 col-md-12 col-sm-12 col-xs-12">
  			<q-card class="bg-white">
  				<q-editor v-model="model" />
				</q-card>
  		</div>
  	</div>
  </div>
</template>

<script>
export default {
  name: 'home',
  data () {
    return {
    	model: ''
    }
  }
}
</script>

<style>
</style>
