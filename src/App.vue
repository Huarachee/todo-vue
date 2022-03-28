<template>
  <div id="app">
    <div class="to-do-box">
      <div class="to-do-box__header">
        <h1 class="header__title">Напоминалка</h1>
        <TaskField @onAddTask="onAddTask"/>
        <div class="header__content">
          <ListItem 
            v-for="(task, index) in tasks" 
            :key="index"
            :index="index"
            :text="task.text"
            :completed="task.completed"
            @onToggleCompleted="onToggleCompleted"
            @onRemoveTask="onRemoveTask"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>

import TaskField from './components/TaskField.vue'
import ListItem from './components/ListItem.vue'

export default {
  name: 'App',
  data: () => ({
    tasks: [
      {
        text: 'Помыть посуду',
        completed: false,
      },
      {
        text: 'Выгулить собаку',
        completed: false,
      }
    ]
  }),
  methods: {
    onToggleCompleted(index) {  
      this.tasks[index].completed = !this.tasks[index].completed;
    },
    onRemoveTask(index) {
      this.tasks.splice(index, 1);
    },
    onAddTask(text) {
        this.tasks.push({
        text,
        completed: false
      });
    }
  },
  components: {
    TaskField,
    ListItem
  }
}
</script>

<style>
@import './assets/main.css';
</style>
