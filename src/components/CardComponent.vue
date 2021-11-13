<template>
<q-card class="my-card" flat bordered>
  	  		<q-img :src="image" height="120px"></q-img>
		      <q-card-section>
		        <div class="text-overline text-red">{{ rest_class }}</div>
		        <div class="text-h5 q-mt-sm q-mb-xs">{{ name }}</div>
		      </q-card-section>

		      <q-list>
		        <q-item clickable>
		          <q-item-section avatar>
		            <q-icon color="primary" name="home"></q-icon>
		          </q-item-section>
		          <q-item-section>
		            <q-item-label>地址</q-item-label>
		            <q-item-label caption>{{ address }}</q-item-label>
		          </q-item-section>
		        </q-item>

		        <q-item clickable>
		          <q-item-section avatar>
		            <q-icon color="red" name="phone"></q-icon>
		          </q-item-section>
		          <q-item-section>
		            <q-item-label>電話</q-item-label>
		            <q-item-label caption>{{ phone }}</q-item-label>
		          </q-item-section>
		        </q-item>

		        <q-item clickable>
		          <q-item-section avatar>
		            <q-icon color="amber" name="event_available"></q-icon>
		          </q-item-section>
		          <q-item-section>
		            <q-item-label>營業時間</q-item-label>
		            <q-item-label caption>{{ time }}</q-item-label>
		          </q-item-section>
		        </q-item>
		      </q-list>
		      <q-card-actions>
		        <q-btn flat color="dark" label="Location"></q-btn>
		        <q-space></q-space>
		      </q-card-actions>
		    </q-card>
    </template>
<script>
import {defineComponent} from 'vue';

export default defineComponent({
  name: "CardComponent",
  props:{
  	image: {
      type: String,
      required: true
    },
    name: {
      type: String,
      required: true
    },
    rest_class: {
      type: String,
      required: false
    },
    address: {
      type: String,
      required: true
    },
    phone: {
      type: String,
      required: false
    },
    time: {
      type: String,
      required: false
    },
    locate: {
      type: String,
      required: false
    },
  },
})
</script>