<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/>
   <!-- @changeOne="get($event)" -->
  <ButtonCounter :title="ptitle" :alt="imgPath" @hungry='beefNoddle' v-model="lovingVue"  @changeOne="get($event)">
    <!-- <template v-slot:hdmi="{u, user}">
      <input type="text" placeholder="insert into slot" :value='user.ln'>
      {{u.fn}}
    </template> -->

    <!-- 如何访问插槽属性, v-slot, sp 自定义的值 -->
    <!-- <template v-slot:usb1="sp">
      <input type="text" :value="sp.u.ln">
    </template> -->

    <!-- 简写 -->
     <template #hdmi="{u, user}">
       insert into value in hdmi
      <input type="text" placeholder="insert into slot" :value='user.ln'>
      {{u.fn}}
    </template>
  </ButtonCounter>
  <!-- <ButtonCounter /> -->
  <div>
    {{lovingVue}}
    {{message}}
  </div>

    
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import ButtonCounter from './components/Button-Counter.vue'


export default {
  name: 'App',
  components: {
    HelloWorld,
    ButtonCounter
  },
  data:()=>({
    ptitle:"this is parent title",
    imgPath:'//www.baidu.com/img/PCtm_d9c8750bed0b3c7d089fa7d55720d6cf.png',
    message:'default value',
    lovingVue:false
  }),
  methods:{
    beefNoddle:function(){
      // alert("hi, eat it")
      var that  = this
      that.message = "hi, eat it"
    },
    get:function(e){
      //this.lovingVue = !this.lovingVue
      console.log(this.lovingVue+" e->"+e)
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
