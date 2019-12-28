<template>
    <div class="wrapper" ref="wrappers">
    <ul  class="content">
      <button @click="btnClick">按我</button>
      <li>第1个li</li>
      <li>第2个li</li>
      <li>第3个li</li>
      <li>第4个li</li>
      <li>第5个li</li>
      <li>第6个li</li>
      <li>第7个li</li>
      <li>第8个li</li>
      <li>第9个li</li>
      <li>第10个li</li>
      <li>第11个li</li>
      <li>第12个li</li>
      <li>第13个li</li>
      <li>第14个li</li>
      <li>第15个li</li>
      <li>第16个li</li>
      <li>第17个li</li>
      <li>第18个li</li>
      <li>第19个li</li>
      <li>第20个li</li>
      <li>第21个li</li>
      <li>第22个li</li>
      <li>第23个li</li>
      <li>第24个li</li>
      <li>第25个li</li>
      <li>第26个li</li>
      <li>第27个li</li>
      <li>第28个li</li>
      <li>第29个li</li>
      <li>第30个li</li>
      <li>第31个li</li>
      <li>第32个li</li>
      <li>第33个li</li>
      <li>第34个li</li>
      <li>第35个li</li>
      <li>第36个li</li>
      <li>第37个li</li>
      <li>第38个li</li>
      <li>第39个li</li>
      <li>第40个li</li>
      <li>第41个li</li>
      <li>第42个li</li>
      <li>第43个li</li>
      <li>第44个li</li>
      <li>第45个li</li>
      <li>第46个li</li>
      <li>第47个li</li>
      <li>第48个li</li>
      <li>第49个li</li>
      <li>第50个li</li>
      <li>第51个li</li>
      <li>第52个li</li>
      <li>第53个li</li>
      <li>第54个li</li>
      <li>第55个li</li>
      <li>第56个li</li>
      <li>第57个li</li>
      <li>第58个li</li>
      <li>第59个li</li>
      <li>第60个li</li>
      <li>第61个li</li>
      <li>第62个li</li>
      <li>第63个li</li>
      <li>第64个li</li>
      <li>第65个li</li>
      <li>第66个li</li>
      <li>第67个li</li>
      <li>第68个li</li>
      <li>第69个li</li>
      <li>第70个li</li>
      <li>第71个li</li>
      <li>第72个li</li>
      <li>第73个li</li>
      <li>第74个li</li>
      <li>第75个li</li>
      <li>第76个li</li>
      <li>第77个li</li>
      <li>第78个li</li>
      <li>第79个li</li>
      <li>第80个li</li>
      <li>第81个li</li>
      <li>第82个li</li>
      <li>第83个li</li>
      <li>第84个li</li>
      <li>第85个li</li>
      <li>第86个li</li>
      <li>第87个li</li>
      <li>第88个li</li>
      <li>第89个li</li>
      <li>第90个li</li>
      <li>第91个li</li>
      <li>第92个li</li>
      <li>第93个li</li>
      <li>第94个li</li>
      <li>第95个li</li>
      <li>第96个li</li>
      <li>第97个li</li>
      <li>第98个li</li>
      <li>第99个li</li>
      <li>第100个li</li>
    </ul>
    </div>
</template>

<script>
import BScroll from 'better-scroll'

export default {
  name:'Category',
  data(){
    return {
      scroll:null
    }
  },
  mounted(){
    //默认情况下Bscroll是不可以实时的监听滚动位置
    //如果想监听，那么在配置的时候要传入一个属性
    //probeType:0 || 1 || 2 || 3
    //0,1都是不侦测实时的位置
    //2：在手指滚动的过程中侦测，手指离开后的惯性滚动过程中不侦测
    //3：只要是滚动，都侦测
  // this.scroll = new BScroll(this.$refs.wrappers,{
  //   probeType:3,
  //   click:true,
  //   pullUpLoad:true //配置底部上拉有回调函数
  //   })
  //   this.scroll.on('scroll',(position)=>{
  //     // console.log(position)
  //   })
  //    this.scroll.on('pullingUp',()=>{ //监听底部上拉的回调函数
  //     console.log('上拉加载更多')
  //     //因为这个函数只会触发一次，所以要在这里处理两件事
  //     //第一件事：在这里发送网络请求，获取更多页的数据
  //     //第二件事: 等数据请求王朝，并且将新的数据展示出来后，调用
  //     //this.scroll.finishPullUp()这个事件，重置这个pullingUp
  //   })
  },
  methods:{
    btnClick(e){
      console.log(e)
    }
  }
}
</script>

<style scoped>
.wrapper{
  height: 300px;
  overflow: hidden;
}
</style>