<script setup>
import { onMounted, ref } from 'vue';
import TodoItem from './components/TodoItem.vue';


const todoLists = [
  {
    id:crypto.randomUUID(),
    text:'Comer'
  },
  {
    id: crypto.randomUUID(),
    text: 'Saltar'
  }
]

//Esto se ejecuta cuando se monta
onMounted(()=>{
  todoList.value= todoLists
})

// Variables radiactivas
const todoList = ref([])
const formValue = ref('')

const add=()=>{
  if(formValue.value.trim()==='') return;
  const newValue = {
    id:crypto.randomUUID(),
    text: formValue.value
  }
  todoList.value.push(newValue)
  formValue.value=''
}
// const delete=()=>{
//   todoList.value= todoList.value;
// }
const lista=[]

</script>

<template>
  <div class="container">
    <div class="containerTodo">
      <h1 class="containeTodotitle">Todo</h1>
      <div class="containerTodoInput">
        <form @submit.prevent >
          <input
            type="text"
            class="containerInput"
            placeholder="To eat"
            v-model="formValue"
          >
          <button
            class="containerButton"
            @click="add"
            type="sumbit"
          >
            Add
          </button>
        </form>
      </div>
      <div class="containerTodoList">
        <div v-for="todo in todoList">
          <TodoItem :todo="todo" />
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
  .container{
    background-color: #ccc;
    width: 100wh;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .containerTodo{
    width: 80%;
    max-width: 360px;
    background-color: rgba(255,255,255,0.7);
    border-radius: 10px;
    padding: 12px;
    height: 70%;
    display: flex;
    justify-content: flex-start;
    align-items: center;
    flex-direction: column;
  }
  .containeTodotitle{
    text-align: center;
    font-size: 3em;
  }
  .containerTodoInput{
    padding: 6px;
    display: flex;
    gap: 8px;
  }
  .containerInput{
    padding: 6px 4px;
    border-radius: 8px;
    outline: none;
    border: 1px solid #ccc;
  }
  .containerButton{
    border: 1px solid #ccc;
    background-color: rgba(255,252,255,0.9);
    border-radius: 6px;
    padding: 7px;
    cursor: pointer;
    transition: all 0.3s ease-in-out;
    &:hover{
      background-color: rgba(30, 68, 191, 0.5);
      color: white;
    }
  }
</style>
