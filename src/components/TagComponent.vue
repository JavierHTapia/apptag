<template>
  <div class="inputTag">
    <div class="tags">
      <div class="tag" v-for="(tag,index) in tags" :key="index">
        {{ tag }}

      </div>
    </div>
    <input type="text">
  </div>
</template>

<script>
export default {
  name: 'TagComponent',
  data(){
    return{currentValue:'',
    tags:[],
    }
  }


}
</script>


<style scoped>

</style>
