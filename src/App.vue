<template>
  <img alt="Vue logo" src="./assets/logo.png"/>
  <h2>欢迎来到快乐星球</h2>
   <div> 
      <modal />
     <div v-if="loading">Loading。。。。</div>
     <img v-if="loaded" :src="result.imgUrl" />
     </div>
</template>
<script lang="ts">
import useUrlAxios from './hooks/useURLAxios'
import modal from './components/Modal.vue'
export default {
  name: 'App',
  components: {modal},
  setup(){
const {result,loading,loaded,error} = useUrlAxios("https://apiblog.jspang.com/default/getGirl");

return{result,loading,loaded,error}
}
}
</script>