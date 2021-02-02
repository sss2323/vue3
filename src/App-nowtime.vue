<template>
  <img alt="Vue logo" src="./assets/logo.png"/>
  <h2>欢迎来到快乐星球</h2>
   <div> 
     <div>{{nowTime}}</div>
     <button @click="getNowTime">点击显示当前时间</button>
     </div>
</template>
<script lang="ts">
import {nowTime,getNowTime} from './hooks/useNowTime'
import useUrlAxios from './hooks/useURLAxios'
export default {
  name: 'App'
  ,
  setup(){

  
return{
  nowTime,
  getNowTime,
}
}
}
//Ref, reactive  作用一样，都是把普通数据，在模板中变成有响应能力的数据。
//生命周期
//钩子函数
//setup()
//onActivated()  <keep-alive></keep-alive>
//onDeactivated()
//onErrorCaptured()
//onRenderTracked onRenderTriggered
</script>