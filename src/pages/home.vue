<template lang="html">
<div class="container">
  <home-header></home-header> <!-- 展示引入的header组件-->

  <div class="content">
    <ul class="cont-ul">
      <!-- list组件展示区，并用v-for来将数据遍历，:xx="xxx" 是用来给子组件传递数据的 -->
      <list v-for="item of items" :price="item.price" :title="item.title" :img="item.img"></list>
    </ul>
  </div>

  <common-footer></common-footer>
</div>
</template>

<script>
import HomeHeader from '../components/homeHeader'
import CommonFooter from '../components/commonFooter'
import List from '../components/list'

export default {
  data() {
    return {
      items:[] /* 定义一个空数组数据itmes*/
    }
  },
  components:{
    HomeHeader,
    CommonFooter,
    List
  },
  created(){ /* 这个是vue的钩子函数，当new Vue()实例创建完毕后执行的函数 */
    // this.$http.get('http://222.211.86.180:88/api/Vue/get').then((data)=>{
    //    this.items=data.body.goods;
    // })
     this.$http.get('http://47.95.232.44:8088/api/Vue/get').then((result)=>{
       this.items=JSON.parse(result.body).goods;
       console.log(JSON.parse(result.body).goods);
       console.log(JSON.parse(result.body).goods);
     })
  }
}
</script>

<style>
.container {
    width: 100%;
    margin: 0 auto;
  }
  .content {
    margin-bottom: 1.8rem;
  }
  .cont-ul {
    padding-top: 0.5rem;
    background-color: #ccc;
  }
  .cont-ul::after {
    content: '';
    display: block;
    clear: both;
    width: 0;
    height: 0;
  }
</style>
