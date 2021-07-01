<template>
 <loading v-model:active="isLoading"
                 :can-cancel="true"
                 :on-cancel="onCancel"
                 :is-full-page="fullPage"
                 :background-color="'white'"
                 :opacity ="'1'"
                 />
<myNav></myNav>
<myContent :reservoirData="northData" :percentageData="northPercentage" :place="'north'">北部</myContent>
<myContent :reservoirData="midData" :percentageData="midPercentage" :place="'mid'" >中部</myContent>
<myContent :reservoirData="southData" :percentageData="southPercentage" :place="'south'">南部</myContent>
<myFooter></myFooter>
</template>

<script>
import myNav from './components/Mynav'
import myContent from './components/Content'
import myFooter from './components/Footer'
import axios from 'axios';
import Loading from 'vue-loading-overlay';
import 'vue-loading-overlay/dist/vue-loading.css';
export default {
  name: 'App',
  data(){
    return {
      fullPage: true,
      onCancel:true,
      isLoading:true,
      waterData:'',
      northData:[],
      midData:[],
      southData:[],
      northPercentage:[],
      midPercentage:[],
      southPercentage:[]
    }
  },
  components: {
    myNav,
    myContent,
    myFooter,
    Loading
  },
  methods:{
    getNorthData(){
      this.northData.push(this.waterData['新山水庫'])
      this.northData.push(this.waterData['翡翠水庫'])
      this.northData.push(this.waterData['石門水庫'])
      this.northPercentage.push(this.waterData['新山水庫']['percentage'])
      this.northPercentage.push(this.waterData['翡翠水庫']['percentage'])
      this.northPercentage.push(this.waterData['石門水庫']['percentage'])
    },
    getMidData(){
      this.midData.push(this.waterData['永和山水庫'])
      this.midData.push(this.waterData['寶山水庫'])
      this.midData.push(this.waterData['寶山第二水庫'])
      this.midData.push(this.waterData['明德水庫'])
      this.midData.push(this.waterData['鯉魚潭水庫'])
      this.midData.push(this.waterData['德基水庫'])
      this.midData.push(this.waterData['石岡壩'])
      this.midData.push(this.waterData['日月潭水庫'])
      this.midData.push(this.waterData['霧社水庫'])
      this.midData.push(this.waterData['湖山水庫'])
      this.midPercentage.push(this.waterData['永和山水庫']['percentage'])
      this.midPercentage.push(this.waterData['寶山水庫']['percentage'])
      this.midPercentage.push(this.waterData['寶山第二水庫']['percentage'])
      this.midPercentage.push(this.waterData['明德水庫']['percentage'])
      this.midPercentage.push(this.waterData['鯉魚潭水庫']['percentage'])
      this.midPercentage.push(this.waterData['德基水庫']['percentage'])
      this.midPercentage.push(this.waterData['石岡壩']['percentage'])
      this.midPercentage.push(this.waterData['日月潭水庫']['percentage'])
      this.midPercentage.push(this.waterData['霧社水庫']['percentage'])
      this.midPercentage.push(this.waterData['湖山水庫']['percentage'])
    },
    getSouthData(){
      this.southData.push(this.waterData['仁義潭水庫'])
      this.southData.push(this.waterData['蘭潭水庫'])
      this.southData.push(this.waterData['白河水庫'])
      this.southData.push(this.waterData['曾文水庫'])
      this.southData.push(this.waterData['烏山頭水庫'])
      this.southData.push(this.waterData['南化水庫'])
      this.southData.push(this.waterData['阿公店水庫'])
      this.southData.push(this.waterData['牡丹水庫'])
      this.southPercentage.push(this.waterData['仁義潭水庫']['percentage'])
      this.southPercentage.push(this.waterData['蘭潭水庫']['percentage'])
      this.southPercentage.push(this.waterData['白河水庫']['percentage'])
      this.southPercentage.push(this.waterData['曾文水庫']['percentage'])
      this.southPercentage.push(this.waterData['烏山頭水庫']['percentage'])
      this.southPercentage.push(this.waterData['南化水庫']['percentage'])
      this.southPercentage.push(this.waterData['阿公店水庫']['percentage'])
      this.southPercentage.push(this.waterData['牡丹水庫']['percentage'])
    }
  },
  created() {
    const api = `https://script.google.com/macros/s/AKfycbxTtz5XuUse7n2TwgBnuETpg0SX-_93Ns60nnNEo1dv7xEViOUxGUFUlRTNPvTiNRwv/exec`;
    axios.get(api).then(res => {
      this.waterData = res.data;
      this.isLoading=false;
      this.getNorthData();
      this.getMidData();
      this.getSouthData()
    });
    const reservoirList = ['新山水庫', '翡翠水庫', '石門水庫', '永和山水庫', '寶山水庫', '寶山第二水庫', '明德水庫', '鯉魚潭水庫'
            , '德基水庫', '石岡壩', '日月潭水庫', '霧社水庫', '湖山水庫', '仁義潭水庫', '蘭潭水庫'
            , '白河水庫', '曾文水庫', '烏山頭水庫', '南化水庫', '阿公店水庫', '牡丹水庫']
    console.log(reservoirList)
  }
}
</script>

<style>
*{
  margin: 0;
  padding: 0;
  text-decoration: none;
}
#app {
  margin: 0;
  padding: 0;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
