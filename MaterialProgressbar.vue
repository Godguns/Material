<template>
  <div class="hello">
    <svg style="transition: 1s;" width="500" height="500" viewBox="0 0 500 500">
      <defs>
        <linearGradient x1="0" y1="0" x2="0" y2="1" id="all-gradient1">
          <stop offset="0%" stop-color="#15e527" />
          <stop offset="100%" stop-color="#0951e1" />
        </linearGradient>
        <linearGradient x1="0" y1="0" x2="0" y2="1" id="all-gradient2">
          <stop offset="0%" stop-color="#F4392B" />
          <stop offset="100%" stop-color="#f87038" />
        </linearGradient>
        <linearGradient x1="0" y1="0" x2="1" y2="0" id="all-gradient3">
          <stop offset="0%" stop-color="#F86A36" />
          <stop offset="100%" stop-color="#FFCE4E" />
        </linearGradient>
      </defs>
      <circle
        transition="1"
        cx="250"
        cy="250"
        r="100"
        id="c1"
        v-if="this.msg !== 0"
        stroke-dasharray="628,628"
        stroke="url(#all-gradient2)"
        fill="transparent"
        :stroke-dashoffset="progress2"
        stroke-linecap="round"
        stroke-width="50"
      />
      <circle
        cx="250"
        cy="250"
        r="150"
        id="c2"
        stroke-dashoffset="-550"
        stroke="url(#all-gradient2)"
        stroke-dasharray="1200"
        fill="transparent"
        stroke-linecap="round"
        stroke-width="2"
      />
      <text x="185" y="250" fill="gray">run</text>
      <text x="210" id="pro" y="260" fill="black">{{progress1}}%</text>
    </svg>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: Number
  },
  data(){
    return {
      progress1:0,
      progress2:628,
      timer:null
    }
  },
  watch:{
    progress1:{
      handler(val){
        if(this.msg === 0){
          clearInterval(this.timer)
          this.progress1 = 0;
          this.progress2 =628;
        }
                        if(val === this.msg){
        clearInterval(this.timer)
      }

    },
    deep:true, //true 深度监听
    immediate: true
    
    }
  },
  mounted(){
 this.timer =  setInterval(() => {
    this.progress1=this.progress1+1;
    this.progress2 = this.progress2-6.08;
  }, 20);


}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#pro {
  font-size: 45px;
}
#c1 {
  animation-fill-mode: forwards;
  animation: mymove 2s;
}
#c2 {
  animation-fill-mode: forwards;
  animation: mymove2 3.7s;
}
@keyframes mymove {
  from {
    stroke: url(#all-gradient1);
    /* stroke-dashoffset: 528; */
  }
  to {
    stroke: url(#all-gradient2);
    /* stroke-dashoffset: 0; */
  }
}
@keyframes mymove2 {
  from {
    stroke: url(#all-gradient1);
    stroke-dashoffset: 500;
  }
  to {
    stroke: url(#all-gradient2);
    stroke-dashoffset: -550;
  }
}
</style>
