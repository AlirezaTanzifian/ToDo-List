<template>
  <div class="box-body" id="scroll">
    <div class="box-item">
      <ul class="task-list">
        <li v-for="(task, index) in tasks" :key="index">
          <Task :tak="task" @delete="deleteTask(index)" @done="doneTask(index)" @edit="editTask(index)" v-if="task.status"/>
          <Edit :tak="task" @confirm="confirm" @cancel="cancel" v-else-if="!task.status"/>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import Task from "@/components/Task";
import Edit from "@/components/Edit";

export default {
  name: "Box-body",
  components:{
    Task,
    Edit
  },
  data(){
    return{
      test : this.tasks
    }
  },
  props:["tasks"],
  methods:{
    deleteTask(i){
      this.test.splice(i,1)
      console.log(i,this.test)
    },
    doneTask(i) {
      this.test[i].completed = !this.test[i].completed
      console.log(this.test[i].completed)
    },
    editTask(i){
      this.test[i].status = false
    },
    confirm(value){
      let index = value.id
      this.test[index].title = value.title
      this.test[index].status = true
    },
    cancel(value){
      let index = value.id
      this.test[index].title = value.title
      this.test[index].status = true
    }
  }
}
</script>


<style scoped>

.box-body{
  margin: 3px;
  height: 13rem;
  overflow-y: auto;

}

::-webkit-scrollbar {
  width: 10px;
}

/* Track */
::-webkit-scrollbar-track {
  box-shadow: inset 0 0 5px grey;
  border-radius: 10px;
}

/* Handle */
::-webkit-scrollbar-thumb {
  background: #354196;
  border-radius: 10px;
}

/* Handle on hover */
::-webkit-scrollbar-thumb:hover {
  background: #283593;
}

ul{
  padding: 0;
  margin: 0;
}

li{
  list-style: none;
}

</style>