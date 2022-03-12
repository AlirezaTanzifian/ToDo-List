<template>
  <div class="edit">
    <input type="text" v-model="nvalue.title">
    <button class="confirm" @click="confirm()">
      <svg style="width:24px;height:24px" viewBox="0 0 24 24">
        <path fill="currentColor" d="M21,7L9,19L3.5,13.5L4.91,12.09L9,16.17L19.59,5.59L21,7Z" />
      </svg>
    </button>
    <button class="cancel" @click="cancel()">
      <svg style="width:24px;height:24px" viewBox="0 0 24 24">
        <path fill="currentColor" d="M19,6.41L17.59,5L12,10.59L6.41,5L5,6.41L10.59,12L5,17.59L6.41,19L12,13.41L17.59,19L19,17.59L13.41,12L19,6.41Z" />
      </svg>
    </button>
  </div>
</template>

<script>
export default {
  name: "Edit-component",
  props:["tak","Index"],
  data(){
    return{
      ovalue : {id:this.Index, title:this.tak.title},
      nvalue : {id:this.Index, title:this.tak.title}
    }
  },
  methods:{
    confirm(){
      if(this.nvalue.title != ""){
        this.$emit('confirm', this.nvalue)
      }
      else{
        alert("Task can not be empty")
      }
    },
    cancel(){
      this.$emit('cancel', this.ovalue)
    }
  }
}
</script>

<style scoped>

.edit{
  background-color: #706fd3;
  border: #40407a solid 2px;
  border-radius: 5px;
  padding: 5px;
  display: flex;
  align-items: center;
  margin: 12px;
}

input{
  width: 100%;
  background-color: #706fd3;
  border: none;
  outline: none;
}

button{
  margin-right: 3px;
  border-radius: 5px;
  padding: 1px;
}

.confirm{
  background-color: lightgreen;
  border: lightgreen;
}

.cancel{
  background-color: lightcoral;
  border: lightcoral;
}

</style>