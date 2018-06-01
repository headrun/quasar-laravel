<template>
  <div class="ABOUT" align="center">
  	<q-card class="bg-white q-mb-md">
  		<h6>Table Component</h6>
  	</q-card>
		<q-table
			class="bg-white"
	    title="Table Title"
	    :data="tableData"
	    :columns="columns"
	    row-key="name"
	  >
	  	<template slot="top-right" slot-scope="props">
        <q-search
          color="secondary"
          v-model="filter"
          class="col-12"
        />
      </template>
	  </q-table>
  </div>
</template>

<script>
export default {
  name: 'about',
  data () {
    return {
    	filter: '',
    	columns: [
	      {
	        name: 'name',
	        required: true,
	        label: 'Name',
	        align: 'center',
	        field: 'name',
	        sortable: true
	      },
	      {
	        name: 'desc',
	        required: true,
	        label: 'Dessert (100g serving)',
	        align: 'center',
	        field: 'desc',
	        sortable: true
	      },
	      {
	        name: 'phoneno',
	        required: true,
	        label: 'Phone Number',
	        align: 'center',
	        field: 'phoneno',
	        sortable: true
	      },
	    ],
	    tableData: [
	      {
	        name: 'Frozen Yogurt',
	        desc: 159,
	        phoneno: 6.0,
	      },
	      {
	        name: 'Frozen Yogurt1',
	        desc: 159,
	        phoneno: 6.0,
	      },
	      {
	        name: 'Frozen Yogurt2',
	        desc: 159,
	        phoneno: 6.0,
	      },
	    ]
    }
  },
  created () {}
}
</script>

<style>
</style>
