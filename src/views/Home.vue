<template>
  <AddTask v-show="showAddTask" @add-task="addTask" />
  <Tasks @delete-task="deleteTask" :tasks="tasks" />
</template>

<script>
import Tasks from '../components/Tasks'
import AddTask from '../components/AddTask'
export default {
  name: 'Home',
  props: {
    showAddTask: Boolean,
  },
  components: {
    Tasks,
    AddTask,
  },
  data() {
    return {
      tasks: [],
    }
  },
  methods: {
    addTask(task) {
      task.id = Date.now()

      this.tasks = [...this.tasks, task]
    },
    deleteTask(id) {
      if (confirm('Are you sure?')) {
        this.tasks = this.tasks.filter((task) => task.id !== id)
      }
    },
  },
  created() {
    this.tasks = [
      // Add more tasks as needed
    ]
  },
}
</script>
