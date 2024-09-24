<template>
<form action="" @submit.prevent="addTodo">
  <fieldset role="group">
    <input
      v-model="newTodo"
      type="text"
      placeholder="Tâche à effectuer">
      <button :disabled="newTodo.length == 0">Ajouter</button>
  </fieldset>
</form>
  <div v-if="todos.length == 0"> Vous n'avez pas de tâche à faire :(</div>
  <div v-else>
    <ul>
      <li v-for="todo in sortedTodo"
      :key="todo.date"
      :class="{completed: todo.completed}"
      >
      <Checkbox :label="todo.title" 
      @check="console.log('coché')" 
      @uncheck="console.log('décoché')" 
      />
    </li>
    </ul>
    <label>
      <input type="checkbox" v-model="hideCompleted">
      Masquer les tâches complétées
    </label>
    <p v-if="remainingTodos > 0">
        {{ remainingTodos }} tâche{{ remainingTodos > 1 ? 's' : '' }} à faire
      </p>
      <Checkbox :label="'Checkbox composant dynamique'"/>
  </div>
</template>

<script setup>
import { computed, ref } from 'vue';
import Checkbox from './Checkbox.vue'

const todos = ref([{
  title: 'Tâche de test',
  completed: true,
  date: 1,

},{
  title: 'Tâche de test',
  completed: false,
  date: 2,

}])

const newTodo = ref('')

const hideCompleted = ref(false)

const addTodo = () => {
  todos.value.push({
    title: newTodo.value,
    completed: false,
    date: Date.now()
  })
  newTodo.value= ''
}

const sortedTodo = computed(() => {
  const sortedTodos = todos.value.toSorted((a,b) => a.completed > b.completed ? 1 : -1)
  if(hideCompleted.value == true){
    return sortedTodos.filter(t => t.completed == false )
  }
  return sortedTodos
  
})

const remainingTodos = computed(() => {
  return todos.value.filter(t => t.completed == false).length
})
</script>

<style>
.completed {
  opacity: .5;
  text-decoration: line-through;
}
</style>