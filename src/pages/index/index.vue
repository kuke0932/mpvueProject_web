<template>
  <div class="container" @click="clickHandle('test click', $event)" >
    <!--订单-->
    <div class="order-top">
      <h2>订单</h2>
    </div>
    <!--订单详情-->
    <div class="orderDetail" v-for="(item, index) in list" v-bind:key="index" id="myVue" >
      <div class="orderWhip">
        <p>下单时间</p>
        <span>{{item.time}}</span>
      </div>
      <div class="orderWhip">
        <p>快递单号</p>
        <span>{{item.num}}</span>
      </div>
      <div class="orderWhip">
        <p id="ddxx">订单信息</p>
        <span id="xxqk">{{item.name}}</span>
      </div>
      <div class="orderWhip">
        <navigator url="/pages/index/status">
          <p>订单状态</p>
          <span>{{item.info}}</span>
          <img src="/images/header_pic.jpg" alt="">
          <image src="/images/header_pic.jpg"></image>
          <!--<image src='/images/details3.png'></image>-->
        </navigator>
      </div>
    </div>
  </div>
</template>

<script>
//  import card from '@/components/card'

export default {
  data () {
    return {
      list: [
        {
          time: '2018/5/24',
          num: '454545567554546545',
          name: '【18款大众速腾 AD92黑色全包+黑灰丝圈】 JY33真皮方向盘套',
          info: '已签收'
        },
        {
          time: '2018/5/24',
          num: '454545567554546545',
          name: '【18款大众速腾 AD92黑色全包+黑灰丝圈】 JY33真皮方向盘套',
          info: '已签收'
        },
        {
          time: '2018/5/24',
          num: '454545567554546545',
          name: '【18款大众速腾 AD92黑色全包+黑灰丝圈】 JY33真皮方向盘套',
          info: '已签收'
        }
      ]
    }
  },
  created () {
    // 调用应用实例的方法获取全局数据
    this.getUserInfo()
  },
  methods: {
    bindViewTap () {
      const url = '../logs/main'
      wx.navigateTo({ url })
    },
    getUserInfo () {
      // 调用登录接口
      wx.login({
        success: () => {
          wx.getUserInfo({
            success: (res) => {
              this.userInfo = res.userInfo
            }
          })
        }
      })
    },
    clickHandle (msg, ev) {
      console.log('clickHandle:', msg, ev)
    }
  }
}
</script>

<style scoped>

  /*订单页*/
  .order-top{
    width:100%;
    height: 1rem;
    background: #6A7D8F;
    float: left;
  }
  .order-top h2{
    text-align: center;
    color: #fff;
    line-height: 1rem;
    float: left;
    width: 100%;
  }
  .orderDetail{
    width: 100%;
    height: auto;
    border-top: 1px solid #8B9CAC;
    margin-top: 20px;
    border-bottom: 1px solid #8B9CAC ;
    float: left;
  }
  .orderWhip{
    width:100%;
    float: left;
    height: auto;
  }
  .orderWhip p{
    float: left;
    padding-right: 10%;
    line-height: 1rem;
    padding-left: 2%;
    height: auto;
  }
  .orderWhip span{
    height: auto;
    line-height: 1rem;
  }
  #ddxx{
    float: left;
    height: 2rem;
    width: auto;
  }
  #xxqk{
    display: -webkit-box;
    -webkit-line-clamp: 2;
    -webkit-box-orient: vertical;
    overflow: hidden;
    display: block;
    height: 2rem;
    width: auto;
  }
</style>
