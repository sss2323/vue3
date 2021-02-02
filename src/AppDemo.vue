<template>
  <img alt="Vue logo" src="./assets/logo.png"/>
  <h2>欢迎来到快乐星球</h2>
   <div> 
     <button 
     v-for="(item,index) in girls" v-bind:key="index" @click="selectGirlFun(index)">【{{index}}】{{item}}</button>
     <div>你选择了哪位管家【{{selectGirl}}】为您服务</div>
     <button @click="overAction">选择完毕</button>
     <div>{{overText}}</div>
     </div>
</template>
<script lang="ts">
import {
  // defineComponent,
   ref,
reactive,
toRefs,
onBeforeMount,
onMounted,
onRenderTracked,
onRenderTriggered,
watch,
} from 'vue';
interface DataProps{
  girls: string[];
  selectGirl: string;
  selectGirlFun: (index:  number) => void;

}
export default {
  name: 'App',
  setup(){
    console.log("1,开始创建组件------setup()")
    const data: DataProps = reactive({
      girls:["小青","小王","小仙"],
      selectGirl:"",
      selectGirlFun:(index: number) => {
      data.selectGirl = data.girls[index];

      }
    })
    // const girls = ref(["小青","小王","小仙"]);
    // const selectGirl = ref("");
    // const selectGirlFun =(index: number)=  >{
    //         selectGirl.value = girls.value[index];
    // };

    // onBeforeMount(()=>{
    // console.log("2,组件挂载到页面之前执行------onBeforeMount()")
    // })
    // onMounted(()=>{
    //       console.log("3,组件挂载到页面之后执行------onMounted()")

    // })
    // onRenderTracked((event)=>{
    //             console.log("4,状态跟踪钩子函数------onRenderTracked()")
    //             console.log(event);
    // })
    // onRenderTriggered((event)=>{
    //                   console.log("5,状态跟踪-----onRenderTriggered()")
    //                                   console.log(event);

    // })
    const refData = toRefs(data);
    const overText = ref("可爱星球")
    const overAction = ()=>{
      overText.value = "选择完成|"+overText.value;
      // document.title = overText.value;
    }
    watch([overText,() => (data.selectGirl)],(newValue,oldValue)=>{
      console.log(`new-----${newValue}`);  
      console.log(`old--${oldValue}`);
      document.title = `${newValue[0]}`;
    });
    return {...refData,overText,overAction}
  }

};

//Ref, reactive  作用一样，都是把普通数据，在模板中变成有响应能力的数据。
//生命周期
//钩子函数
//setup()
//onActivated()  <keep-alive></keep-alive>
//onDeactivated()
//onErrorCaptured()
//onRenderTracked onRenderTriggered
</script>