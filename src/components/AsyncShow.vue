<template>
    <h1>{{result}}</h1>
</template>
<script lang="ts">
import {defineComponent} from "vue"
export default defineComponent({
  setup(){
      return new Promise((reslove,reject)=>{
          setTimeout(() => {
           return reslove({result:"yiyi小星球"})   
          },2000);
      })
  }  
})
</script>