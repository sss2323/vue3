<template>
      <teleport to="#modal">
    <div id="center">
        <h2>快乐星球</h2>
    </div>
      </teleport>
</template>

<script lang="ts">
export default {
    
}
</script>
<style>
 #center{
     width: 200px;
     height: 200px;
     background: white;
     border: solid 1px red;
     position: fixed;
     left: 50%;
     top: 50%;
     margin-left: -100px;
     margin-right: -100px;
 }
</style>