<template>
  <div>
    <div id="Home">
    <Banner></Banner>
    <list></list>
    <Ad v-for='(item,idx) in num' :key='idx' :test=item></Ad>
  </div>
  <bottom></bottom>
  </div>
  

  
  </template>
<script>
import Banner from './banner1.vue'
import List from './list.vue'
import Ad from './ad.vue'
import bottom from '../../Common/Xfooter.vue'


export default {
  name: 'Home',
  components: {
    Banner,List,Ad,bottom
  },
  data(){
  	return{
  		num:[{path:'http://asset.ibanquan.com/image/5a38e429b1b9575cd9000319/s.jpeg?v=1513677865',pm:1},{path:'http://asset.ibanquan.com/image/5a38da3c0dd76c175d0002dc/s.jpeg?v=1513675325',pm:3}]
  	}
  },
  activated(){
        console.log('homehhhh')
}
   
}
</script>

<style lang="less" scoped>
@import url('../../../../node_modules/swiper/dist/css/swiper.min.css');
@import url(../../../styls/main.less);
#Home {

  .margin(45,0,50,0);
}
</style>
