<template>
  <div class="barrage">
    <img src="https://images.pexels.com/photos/2286895/pexels-photo-2286895.jpeg?auto=compress&cs=tinysrgb&dpr=2&w=500" alt="">
    
    <canvas id="myCanvas">
      
    </canvas>
  </div>
</template>
<script>
import barrageEffect from './barrage'
export default {
  data () {
    return {
      imgUrl:'',
      canvasWidth:0,
      canvasHeight:0,
      context:null,
      mobile:0,
      barrage:null,
    }
  },
  methods: {
    init(){
      const fontSize = 20
      const highwayAmount = 4
      this.barrage = new barrageEffect.Barrage('myCanvas',this.canvasWidth,this.canvasHeight,highwayAmount,fontSize)
        //可通过addTest方法不断添加弹幕
        this.barrage.addTest(['风景好美呀','绝了绝了','好想去','安排安排','醒醒醒醒，你没钱去'])
        setTimeout(()=>{
          this.barrage.addTest(['年轻人','耗子尾子','耗耗反思','这是你该做的梦吗','醒醒醒醒，老实搬砖','再做梦别怪我捶你'])
        },500)
    },
    setCanvas(){
      let canvasStyle = document.getElementById('myCanvas')
        this.canvasWidth = canvasStyle.offsetWidth
        this.canvasHeight =canvasStyle.offsetHeight
        this.init()
    }
  },
  computed:{
    
  },
  mounted(){
    this.setCanvas()
  }
};
</script>
<style scoped>
.barrage{
  width: 100vw;
  height: 100vh;
  position: relative;


}
  #myCanvas{
    position: absolute;
    z-index: 2;
    width: 565px;
    height: 377px;
    top: 0;
    left: 0;
  }
    img{
    width: 565px;
    height: 377px;
  }
</style>
