<template>
	<q-layout view="hHh lpR fFf">

	<q-page class="flex flex-center">

    <q-header elevated class="bg-black text-white">
      <q-toolbar>
        <div class="col-md-1"></div>
        <q-toolbar-title class="col-md-2">
          Dream Tourist
        </q-toolbar-title>


      <q-select dark v-model="model" :options="options" label="請選擇縣市" class="col-md-3"></q-select>
      <q-btn
      label="送出"
      type="submit"
      color="white"
      text-color="black"
      @click="sendQuery"
      v-close-popup
      class="col-md-1"
      />
      </q-toolbar>
       <div class="col-md-3"></div>
    </q-header>
		<div class="q-pa-md row items-start q-gutter-md q-mt-xl">
			<CardTemplate v-for="(item,id) in data_list" 
			:image="item.Picture.PictureUrl1"
			:name="item.Name"
			:address="item.Address"
			:rest_class="item.Class"
			:phone="item.Phone"
			:time="item.OpenTime"
			:key="id"> </CardTemplate>
		</div>
	</q-page>
	</q-layout>
</template>

<script>
import { defineComponent, ref } from 'vue'
import { api } from 'boot/axios';
import CardTemplate from 'src/components/CardComponent.vue'

export default defineComponent({
  name: 'MainPage',
  components: { CardTemplate },
  data() {
  	return {
  	data_list: [],
  	options: [
         { label: '基隆市', value: 'Keelung' },
         { label: '臺北市', value: 'Taipei' },
         { label: '新北市', value: 'NewTaipei' },
         { label: '桃園市', value: 'Taoyuan' },
         { label: '新竹縣', value: 'HsinchuCounty' },
         { label: '新竹市', value: 'Hsinchu' },
         { label: '苗栗縣', value: 'MiaoliCounty' },
         { label: '台中市', value: 'Taichung' },
         { label: '彰化縣', value: 'ChanghuaCounty' },
         { label: '南投縣', value: 'NantouCounty' },
         { label: '雲林縣', value: 'YunlinCounty' },
         { label: '嘉義縣', value: 'ChiayiCounty' },
         { label: '嘉義市', value: 'Chiayi' },
         { label: '臺南市', value: 'Tainan' },
         { label: '高雄市', value: 'Kaohsiung' },
         { label: '屏東縣', value: 'PingtungCounty' },
         { label: '宜蘭縣', value: 'YilanCounty' },
         { label: '花蓮縣', value: 'HualienCounty' },
         { label: '臺東縣', value: 'TaitungCounty' },
         { label: '連江縣', value: 'LienchiangCounty' },
         { label: '金門縣', value: 'KinmenCounty' },
         { label: '澎湖縣', value: 'PenghuCounty' }
      ],
     model: ref(null),
  }
  },
  mounted () {
  	api.get('/MOTC/v2/Tourism/ScenicSpot?$top=30&$format=JSON&$filter=Picture/PictureUrl1 ne null', null, {
      headers: {
        //'Authorization': 'Bearer '+localStorage.getItem( "factory_token" )
      }
    })
    .then(response => {
    	this.data_list = response.data
    	//console.log(this.data_list)
      })
      .catch(function(err){
      	console.log(err)
      })
  },
  methods: {
    sendQuery: function() {
    api.get('/MOTC/v2/Tourism/ScenicSpot/'+this.model.value+'?$top=30&$format=JSON&$filter=Picture/PictureUrl1 ne null', null, {
      headers: {
      }
    })
    .then(response => {
      this.data_list = response.data
      //console.log(this.data_list)
      })
      .catch(function(err){
        console.log(err)
      })
    }
  }
})
</script>
<style scoped>
.my-card {
  width: 300px;
}
</style>