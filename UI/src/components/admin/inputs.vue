<template>
  <div class="HOME">
  	<q-card class="bg-white q-mb-md" align="center">
  		<h6>All Inputs Component</h6>
  	</q-card>
  	<div class="row gutter-sm q-mb-md">
  		<div class="col-lg-6 col-md-6 col-sm-12 col-xs-12">
  			<q-card class="bg-white">
  				<q-card-title>
  					Color Picker
  				</q-card-title>
  				<q-card-main align="center">
		  			<q-color v-model="modelHex" />
					</q-card-main>
				</q-card>
  		</div>
  		<div class="col-lg-6 col-md-6 col-sm-12 col-xs-12">
  			<q-card class="bg-white">
  				<q-card-title>
  					Date Picker
  				</q-card-title>
  				<q-card-main align="center">
		  			<q-datetime v-model="dateModal" type="date" />
					</q-card-main>
				</q-card>
  		</div>
  	</div>
  	<div class="row gutter-sm q-mb-md">
  		<div class="col-lg-6 col-md-6 col-sm-12 col-xs-12">
  			<q-card class="bg-white">
  				<q-card-title>
  					AutoComplete
  				</q-card-title>
  				<q-card-main align="center">
		  			<q-input color="amber" v-model="terms" placeholder="Type 'fre'">
						  <q-autocomplete
						    @search="search"
						    :min-characters="3"
						    @selected="selected"
						  />
						</q-input>
					</q-card-main>
				</q-card>
  		</div>
  		<div class="col-lg-6 col-md-6 col-sm-12 col-xs-12">
  			<q-card class="bg-white">
  				<q-card-title>
  					Select Box
  				</q-card-title>
  				<q-card-main>
		  			<q-select
				      v-model="select"
				      radio
				     :options="selectOptions"
				    />
					</q-card-main>
				</q-card>
  		</div>
  	</div>
  	<div class="row gutter-sm q-mb-md">
  		<div class="col-lg-6 col-md-6 col-sm-12 col-xs-12">
  			<q-card class="bg-white">
  				<q-card-title>
  					Collapsables
  				</q-card-title>
  				<q-card-main align="left">
  					<q-list inset-separator>
				      <q-collapsible icon="mail" label="Inbox" sublabel="5 unread emails">
				        <div>{{ lorem }}</div>
				      </q-collapsible>
				      <q-collapsible icon="send" label="Outbox" sublabel="Empty">
				        <div>{{ lorem }}</div>
				      </q-collapsible>
				    </q-list>
					</q-card-main>
				</q-card>
  		</div>
  		<div class="col-lg-6 col-md-6 col-sm-12 col-xs-12">
  			<q-card class="bg-white">
  				<q-card-title>
  					File Uploader
  				</q-card-title>
  				<q-card-main align="left">
  					<q-uploader
						  url=""
						  method="PUT"
						  :headers="{ 'x-amz-acl': '', 'content-type': 'csv' }"
						  :url-factory="getSignedUrl"
						  :send-raw="true"
						/>
					</q-card-main>
				</q-card>
  		</div>
  	</div>
  	<blockquote>
		  <p>For all components see below link.</p>
		  <small><a href="https://quasar-framework.org/components/" target="_blank">
		  	https://quasar-framework.org/components/
		  </a></small>
		</blockquote>
  </div>
</template>

<script>
import { uid, filter } from 'quasar'

export default {
  name: 'home',
  data () {
    return {
    	modelHex: '#C7044B',
    	dateModal: new Date(),
    	terms: '',
    	select: '',
    	lorem: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Tempore, nemo minus dolore facere saepe molestias, fugiat officia aspernatur expedita pariatur, accusantium hic exercitationem perspiciatis voluptate possimus nobis temporibus ipsa officiis!',
    	selectOptions: [
        {
          label: 'Google',
          value: 'goog'
        },
        {
          label: 'Facebook',
          value: 'fb'
        }
      ]
    }
  },
  methods: {
    search (terms, done) {
      setTimeout(() => {
        done(filter(terms, {field: 'value', list: parseCountries()}))
      }, 1000)
    },
    selected (item) {
      this.$q.notify(`Selected suggestion "${item.label}"`)
    },
    async getSignedUrl (file) {
		  const contentType = file.type // To send the correct Content-Type
		  const fileName = file.name // If you want to use this value to calculate the S3 Key.
		  const response = await api.getSignedUrl({ fileName, contentType }) // Your api call to a sever that calculates the signed url.
		  return response.data.url
		}
  }
}
</script>

<style>
</style>
