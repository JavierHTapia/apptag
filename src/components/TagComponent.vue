<template>
  <div class="container">
  <h1>Tags</h1>
  <div class="inputTag">
    <div class="tags">
      <div class="tag" v-for="(tag,index) in tags" :key="index">
        {{ tag }}<button @click="deleteTag(tag)"><i class='bx bxs-x-circle' ></i></button>
      </div>
    </div>
    <form action="" @submit.prevent="handleSubmit">
      <input class="input" type="text" placeholder="escriba y presione Enter" v-model="currentValue" @keydown="handleKeyDown">
    </form>
  </div>
</div>
</template>

<script>
export default {
  name: 'TagComponent',
  data(){
    return{currentValue:'', tags:[]
    };
  },
  methods:{
    handleKeyDown(e){
      if(e.key == 'Backspace' && this.currentValue === ""){
        this.tags.pop(this.currentValue);
      }
    },
    handleSubmit(){
      if(this.currentValue !==""){
        /* impedir que se repita un tag */
        const exist = this.tags.some((item)=>item===this.currentValue);
        if(!exist){
        /* adiciona nuevo tag */
        this.tags.push(this.currentValue);
        this.currentValue = "";
        }

      }
    },
    deleteTag(tag){
      this.tags = this.tags.filter((item)=> item !== tag);
    }
  }
}
</script>

<style scoped>
.container{
    height: 50vh;
    margin-inline: 1.5rem;
    display: grid;
    place-items: center;
}
.inputTag{
  background-color: white;
  box-shadow: 0 4px 24px hsla(222, 68%, 12%, .1);
  display: inline-flex;
  border: none;
  border-radius: 4rem;
  padding: 10px;
  height: 45px;
  font-size: 15px;
}
.tags{
  display: flex;
  gap: 3px;
  padding: 5px;
}
.tags .tag{
  display: flex;
  padding: 5px;
  border: solid 1px #ccc;
  gap: 5px;
  align-content: center;
  border-radius: 4rem;
}
.inputTag form{
  display: inline-flex;
}
.inputTag .input{
  background: none;
  border: none;
  outline: none;
  padding: 0 5px;
  font-size: 15px;
}
.tag button{
  background-color:transparent;
  border: none;
  margin: auto;
  font-size: 21px;
}
</style>
