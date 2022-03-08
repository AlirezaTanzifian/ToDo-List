<template>
  <div>
    <div class="text">
      <h1>Vue ToDo List</h1>
      <p><i>Designed by Alireza Tanzifian</i></p>
    </div>
    <div class="box">
      <BoxHeader :tasks="tasks" @deleteAll="deleteAllTask()" @deleteTaskDone="deleteTaskDone"/>
      <hr>
      <BoxBody :tasks="tasks"></BoxBody>
      <BoxFooter @newTask="addTask" :tasks="tasks"/>
    </div>
  </div>
</template>

<script>
import BoxHeader from "@/components/Box-header";
import BoxFooter from "@/components/Box-footer";
import BoxBody from "@/components/Box-body";



export default {
  name: "home-component",
  emits:["newList"],
  components:{
    BoxHeader,
    BoxFooter,
    BoxBody,
  },
  data(){
    return{
      tasks : [
        { id:0, title : "Learn Persian", completed : false, status : true},
        { id:1, title : "Learn English", completed : false, status : true},
        { id:2, title : "Learn Spanish", completed : false, status : true},
        { id:3, title : "Learn French", completed : false, status : true},
        { id:4, title : "Learn Chinese", completed : false, status : true}
      ]
    }
  },
  methods:{
    addTask(value){
      this.tasks.push({id:this.tasks.length, title:value, completed:false, status: true})
    },
    deleteAllTask(){
      this.tasks=[]
      //let l= this.tasks.length
      //this.tasks.splice(0,l)
    },
    deleteTaskDone() {
      let i = 0
      while (i < this.tasks.length) {
        if (this.tasks[i].completed == true) {
          this.tasks.splice(i, 1)
        }
        else {
          i++
        }
      }
    }
  }
}
</script>

<style scoped>

.text{
  text-align: center;
  margin: auto 0;
}

.box{
  display: inline-block;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  height: 350px;
  width: 600px;
  border-radius: 20px;
  background: rgba(255, 255, 255, 0.2);
  backdrop-filter: blur(30px);
  border: 2px solid rgba(255, 255, 255, 0.1);
  box-shadow: 0 0 80px rgba(0, 0, 0, 0.2);
  overflow: hidden;
}

button{
  margin: 2px;
  border-redius: 5px;
}

hr{
  color: white;
  position: center;
  margin: 0;
}
</style>