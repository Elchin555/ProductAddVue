<template>
   <div class="progress">
      <div class="progress-bar bg-info" role="progressbar" :style="{width: widthSize+'%'}" aria-valuenow="50" aria-valuemin="0" aria-valuemax="100">
        {{number}}/10
      </div>
      </div>
</template>

<script>
import {eventBus} from "../main"
export default {
  data(){
    return{
      number:0,
      widthSize:0
    }
  },
  created(){
    eventBus.$on("sendProgressBarData",(e)=>{
      this.number=e
      this.widthSize=e*10
    })
  }
}
</script>