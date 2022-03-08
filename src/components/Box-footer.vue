<template>
  <div class="box-footer">
    <form action="javascript:addTask()" class="box-input">
      <input type="text" placeholder="New Task" v-model="text">
      <button type="submit" @click="addTask()">
        <svg style="width:24px;height:24px" viewBox="0 0 24 24">
          <path fill="currentColor" d="M19,13H13V19H11V13H5V11H11V5H13V11H19V13Z" />
        </svg>
      </button>
    </form>
  </div>
</template>

<script>

export default {
  name: "Box-footer",
  props:["tasks"],
  data(){
    return{
      text : ""
    }
  },
  methods:{
    addTask(){
      if (this.text != ""){
        this.$emit('newTask',this.text)
        this.text = ""
      }
    }
  }
}
</script>

<style scoped>

.box-footer{
  padding: 10px 20px;
}

.box-input{
  display: flex;
  -webkit-box-align: center;
  align-items: center;
  justify-content: center;
  border: 0.3rem solid #1976d2;
  border-radius: 5rem;
  overflow: hidden;
  background-color: #d5faff;
}
input{
  border: none;
  outline: none;
  padding: 0.8rem 1.2rem;
  background-color: #d5faff;
  flex: 1;
  font-size: 1rem;
}
button{
  border-radius: 50%;
  border: none;
  width: 2.5rem;
  height: 2.5rem;
  font-weight: bolder;
  background-color: #1976d2;
  color: white;
  justify-content: center;
  white-space: nowrap;
  margin-right: 5px;
}

</style>