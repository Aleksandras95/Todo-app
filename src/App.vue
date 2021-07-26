<template>
  <div id="app">
    <div class="todo">
      <div class="todo__header">
        <h4>Užduočių sąrašas</h4>
      </div>
      <TaskField @onAddTask = "onAddTask"/>
      <div class="todo__list">
        <ListItem 
        v-for = "(task, index) in tasks" 
        v-bind:key = "index"
        :index = "index" 
        :text = "task.text" 
        :completed = "task.completed"
        @onToggleCompleted = "onToggleCompleted"
        @onRemoveTask = "onRemoveTask"
        />
      </div>
    </div>
  </div>
</template>

<script>
import ListItem from './components/ListItem'
import TaskField from './components/TaskField'
export default {
  name: 'App',
  data: () => (
    {
    tasks: []
  }),
  methods: {
    onToggleCompleted(index) {
      this.tasks[index].completed = !this.tasks[index].completed;
    },
    onAddTask(text) {
      this.tasks.push({
        text,
        completed: false
      });
    },
    onRemoveTask(index) {
      this.tasks.splice(index, 1);
    }
  },
  components: {
    ListItem,
    TaskField
  },
}
</script>

<style>
@import "./assets/styles/app.css";

</style>
