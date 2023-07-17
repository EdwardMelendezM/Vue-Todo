<script setup>
defineProps({
  todo:{
    required:true,
    default:'Onichan',
  }
})
</script>

<template>
  <div class="containerTodoItem">
    <input
      type="text"
      v-model="todo.text"
      class="input_text"
    >
    <div class="containerTodoItemBtn">
      <button>delete</button>
    </div>
  </div>
</template>

<style scoped>
  .containerTodoItem{
    width: 100%;
    display: flex;
    padding: 4px;
    justify-content: space-between;
    align-items: center;

  }
  .containerTodoItemBtn{
    padding: 2px 4px;
  }
  button{
    border: 1px solid #ccc;
    background-color: rgba(255,252,255,0.9);
    border-radius: 6px;
    padding: 7px;
    cursor: pointer;
    transition: all 0.3s ease-in-out;
    &:hover{
      background-color: rgba(5, 5, 5, 0.5);
      color: white;
    }
  }
  .input_text{
    background-color: transparent;
    border: 0;
    outline: none;
  }

</style>