<template>
  <div class="progress" v-if="length != null">
    <div class="progress-bar bg-info" role="progressbar" :style="{width : progress + '%'}" aria-valuenow="50" aria-valuemin="0" aria-valuemax="100">
      {{ length }}/10
    </div>
  </div>
</template>

<script>
import {eventBus} from "../main";

export default {
  name: "Progress",
  data(){
    return{
      length : null,
      progress : null
    }
  },
  created() {
    eventBus.$on("progressBarUpdated",(length)=>{
      this.length = length;
      this.progress = length * 10;
    })
  }
}
</script>

<style scoped>

</style>