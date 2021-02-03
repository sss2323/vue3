<template>
  <img alt="Vue logo" src="./assets/logo.png"/>
  <h2>欢迎来到快乐星球</h2>
   <div> 
      <modal />
     <div v-if="loading">Loading。。。。</div>
     <img v-if="loaded" :src="result.imgUrl" />
     <Suspense>  
       <template #default>
         <!-- <AsyncShow /> -->
         <girl-show />
       </template>
       <template #fallback>loading</template>
     </Suspense>
     </div>
</template>
<script lang="ts">
//Suspense 异步组件
import {onErrorCaptured} from 'vue'
import useUrlAxios from './hooks/useURLAxios'
import modal from './components/Modal.vue'
// import AsyncShow from './components/AsyncShow.vue'
import GirlShow from './components/GirlShow.vue'
export default {
  name: 'App',
  components: {
    modal,
  // AsyncShow,
  GirlShow},
  setup(){
    onErrorCaptured((error)=>{
console.log(`error = >`,error);
return true
    })
const {result,loading,loaded,error} = useUrlAxios("https://apiblog.jspang.com/default/getGirl");

return{result,loading,loaded,error}
}
}
</script>