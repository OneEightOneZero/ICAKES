<template>
  <div id="car">
    <div class="weui-panel__bd">
      <a
        href="javascript:void(0);"
        class="weui-media-box weui-media-box_appmsg"
        v-for="(i,idx) in shuju"
        :key="idx"
      >
        <div class="weui-media-box__hd">
          <img class="weui-media-box__thumb" :src="`${i.imgurl}`">
        </div>
        <div class="weui-media-box__bd">
          <h4 class="weui-media-box__title" v-text="i.ename"></h4>
          <span class="weui-media-box__desc" v-text="i.cname"></span>
          <span class="weui-media-box__desc" v-text="i.miaoshu"></span>
          <span class="weui-media-box__desc" v-text="`￥${i.price/100}`"></span>
          <a class="qty">
            <a class="minus" href="javascript:void(0);">-</a>
            <a class="num">1</a>
            <a class="add" href="javascript:void(0);">+</a>
          </a>
        </div>
        <input type="checkbox">
      </a>
    </div>
    <Loading v-show="true"></Loading>
    <tuijian></tuijian>
  </div>
</template>
<script>
import tuijian from './tuijian.vue'
import Loading from '../../Common/Loading.vue'
export default {
  components:{
    tuijian
  },
  computed: {
    addId() {
      return this.$store.state.slider;
    }
  },
  data() {
    return { shuju: [] };
  },
  methods: {
    async findCool() {

      let data = await this.$axios.get(
        "http://localhost:3000/setting/findUser"
      );
      this.shuju = data.data;
    }
  },
  created() {
    this.findCool();
  }
};
</script>
<style scoped>
#car {
  padding-top: 50px;
}
.weui-panel__bd {
  background: #fff;
}
.qty {
  width: 90px;
  height: 25px;
  background: #f7f7f7;
  display: block;
  border: 1px solid #ccc;
  text-align: center;
  line-height: 25px;
}
.num,
.add,
.minus {
  font-size: 10px;
  color: #000;
  display: block;
  float: left;
}
.add {
  width: 24px;
}
.num {
  width: 40px;
  height: 23px;
  background: #fff;
}
.minus {
  width: 24px;
}
</style>

