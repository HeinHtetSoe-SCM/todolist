<template>
<main>
  <h1>Task board</h1>
  <div class="create-new">
    <input type="text" v-model="newTask" placeholder="Add a new task" @keypress.enter="addTask"> 
    <button @click="addTask">Add</button>
  </div>
  <div class="tasks">
    <Task 
      v-for="(task, i) in $store.state.tasks"
      :key="i"
      :task="task"
    />
  </div>
</main>
</template>

<script>
export default {
  name: 'IndexPage',
  data () {
    return {
      newTask: ''
    }
  },
  methods: {
    addTask () {
      if(this.newTask) {
        this.$store.commit('ADD_TASK', this.newTask);
        this.newTask = '';
      }
    }
  }
}
</script>
