<script setup>
import {ref} from 'vue'

const newTask = ref('')
const tasks = ref([])


/**** ADDING TASK **********/
const addTask = () => {
    if (newTask.value.trim() !== '') {
        tasks.value.push(newTask.value)
        newTask.value = ''
    }
}

/********** REMOVING TASK *************/
const removeTask = (index) => {
    tasks.value.splice(index, 1)
}


</script>

<template>
    <div class="todo-app">
        <div class="task-input">
            <input v-model="newTask" @keyup.enter="addTask" placeholder="Add new Task" />
            <button @click="addTask">Add To Do</button>
        </div>

        <ul class="task-list">
            <li v-for="(task, index) in tasks" :key="index" class="task-item">
            {{ task }}
            <button @click="removeTask(index)" class="remove-button">Remove</button>
           </li>
          
        </ul>
    </div>
</template>

<style scoped>

*{
    margin: 0;
    padding: 0;
    
}

.todo-app{
    border: 2px solid aliceblue;
    max-width: 400px;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

.app-title{
    font-size: 24px;
    margin-bottom: 20px;
    text-align: center;
    color: gray;
}

.task-input{
    display: flex;
    gap: 10px;
}

input{
    flex: 1;
    padding: 8px;
    font-size: 14px;
}

button{
    padding: 8px 12px;
    font-size: 14px;
    background-color: darkcyan;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
}

button:hover{
    background-color:darkgreen;
}

.task-list{
    list-style: none;
    padding: 0;
}

.task-item{
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px;
    margin: 8px;
    background: aliceblue;
    border: 1px solid #ddd;
    border-radius: 4px;
}

.remove-button{
    padding: 6px 10px;
    font-size: 12px;
    background-color: azure;
    color: red;
    border: none;
    border-radius: 3px;
    cursor: pointer;
}

.remove-button:hover{
    background-color: beige;
}



</style>