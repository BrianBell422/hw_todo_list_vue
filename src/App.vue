<template>
  <div id="app">
    <h1>ToDo List</h1>

    <ul class="unordered-list">
      <li v-for="(task, index) in tasks" :key="index" class="list-item">
        <div>Task: {{ task.name }}</div>
        <div>Priority: {{ task.priority }}</div>
        <br>
      </li>
    </ul>

    <form v-on:submit.prevent="saveNewTask">
      <section class="add-task-section">
        <label for="new-task" class="new-task"><h3>Add Task: </h3></label>
        <div class="new-task-wrapper">
          <input id="new-task" type="text" v-model="newTask"/>  
        </div>  
        <h3 class="priority">Priority:</h3>
        <div class="priority-select">
          <input type="radio" id="high" name="priority" value="High" v-model="priority"/>
          <label for="high">High</label><br>

          <input type="radio" id="low" name="priority" value="Low" v-model="priority"/>
          <label for="low">Low</label><br>
        </div>
      </section>

      <input type="submit" value ="Save New Task" />
    </form>
  </div>
</template>

<script>
  export default {
    data(){
      return{
        tasks: [
          {name: "Buy shopping", priority: "High"},
          {name: "Clean bathroom", priority: "Low"},
          {name: "Car's MOT", priority: "High"},
        ],
        newTask: "",
        priority: ""
      }
    },
    methods: {
      saveNewTask: function(){
        this.tasks.push({
          name: this.newTask, 
          priority: this.priority
        });
        this.newTask = "";
        this.priority = "";
      }
    }
  }
</script>

<style>

template {
  
  margin: 0;
  padding: 0;
  background-color: bisque;
}

#app {
  text-align: center;
  font-family: 'Roboto', sans-serif;
  background-color: bisque;
  margin:0;
  padding:0;
}

.unordered-list {
  padding: 0px 0px 0px 0px;
}

.list-item {
  list-style-type: none;
}

.add-task-section {
  display: grid;
  grid-column: 1fr 1fr;
  grid-template-columns: 1fr 1fr;
}

#new-task {
  width: 150px;
  height: 20px;
  margin: auto;
}

.new-task {
  padding-left: 400px;
}

.priority {
  padding-left: 500px;
}

.priority-select {
  padding-right: 500px;
  margin: auto;
}

.new-task-wrapper {
  padding-right: 450px;
  margin: auto;
}







</style>


