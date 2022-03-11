<template>
  <div class="box-header">
    <div>
      <ul>
        <li>
          <span class="tag-name">Tasks</span>
          <span class="tag-value" >{{ allTasks }}</span>
        </li>
        <li>
          <span class="tag-name">Tasks Done</span>
          <span class="tag-value">{{ allTaskDone }}</span>
        </li>
      </ul>
    </div>
    <div>
      <ul>
        <li>
          <button @click="deleteAll()">Delete All Tasks</button>
        </li>
        <li>
          <button @click="deleteTaskDone()">Delete Tasks Done</button>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>

export default {
  name: "Box-header",
  props:["tasks"],
  computed:{
    allTasks(){
      return this.tasks.length
    },
    allTaskDone(){
      return this.tasks.filter(task => task.completed).length
    }
  },
  methods:{
    deleteAll(){
      this.$emit('deleteAll')
    },
    deleteTaskDone(){
      this.$emit('deleteTaskDone')
    }
  }
}
</script>

<style scoped>

.box-header{
  display: flex;
  padding: 0.5rem;
  align-items: center;
  margin: 0;
  flex-wrap: wrap;
  justify-content: center;
}

ul{
  display: flex;
  list-style: none;
  margin: 0;
  padding: 2px;
}

li{
  background-color: #2c2c54;
  padding: 0.2rem;
  border-radius: 0.5rem;
  color: white;
  margin: 0 5px;
}

button{
  background-color:  #2c2c54;
  border:  #2c2c54;
  color: white;
}

.tag-name{
  padding-right: 3px;
}

.tag-value{
  padding: 3px 7px;
  background-color: white;
  color:  #393e46;
  border-radius: 50%;
}


</style>