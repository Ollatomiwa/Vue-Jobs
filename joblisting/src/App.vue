<script setup>
  import { ref } from 'vue';

  const name = ref ('John Doe');
  const status = ref ('active');
  const task = ref (['Task One', 'Task Two', 'Task Three']);

  const newTask = ref('');

  
  const toggleStatus = () => {
    if (status.value === 'active') {
      status.value = 'pending';
    }
    else if (status.value === 'pending'){
      status.value = 'inactive';
    }
    else {
      status.value = 'active';
    }
  }
  const addTask = () => {
    if (newTask.value.trim()!= ''){
      task.value.push(newTask.value)
      newTask.value = '';
    }
  }

  const deleteTask = (index) => {
    task.value.splice(index, 1);
  };

</script>

<template>
  <h1> {{name}}</h1>
  <p v-if ="status === 'active'">user is active</p>
  <p v-else-if ="status === 'pending'">User is pending</p>
  <p v-else> User is inactive</p>  
  
  <form @submit.prevent="addTask">
    <label for = "newTask"> Add Task</label> 
    <input type= "text" id = "newTask" name = "newTask" v-model= "newTask"/>
    <button type = "submit">submit</button>
  </form>    
  <h3> Task: </h3>
  <ul>
    <li v-for = "{task, index} in task" :key ="task">
      <span> {{task}} 
      <button @click="deleteTask (index)"></button>
      </span>
    </li>
  </ul>  
  <br>

  <button @click="toggleStatus">change status</button>
</template>

