<template>
  <div id='app'>
    <h1>My Vue To Do List</h1>
    <ToDoList :items="items" @finish="finishItem" @remove="removeItem" />
    <ToDoForm @add="addItem" />
  </div>
</template>

<script>
import ToDoForm from '@/components/ToDoForm.vue'
import ToDoList from '@/components/ToDoList.vue'
// import ToDoList from '@/components/FunctionalToDoList.vue'

export default {
  name: 'app',
  components: { ToDoForm, ToDoList },
  data() {
    return {
      items: [
        {
          id: 0,
          content: 'Make a presentation',
          isFinished: false
        },
        {
          id: 1,
          content: 'Give a presentation',
          isFinished: false
        },
        {
          id: 2,
          content: 'Take questions',
          isFinished: false
        },
        {
          id: 3,
          content: 'Get applause',
          isFinished: false
        },
      ]
    }
  },
  methods: {
    addItem(content) {
      if (!content) {
        return;
      }
      const item = {
        id: new Date().getTime(),
        isFinished: false,
        content
      };
      this.items = [...this.items, item];
    },
    removeItem(id) {
      this.items = this.items.filter(item => item.id !== id);
    },
    finishItem(id) {
      const finishedItem = this.items.find(item => item.id === id);
      this.$set(finishedItem, 'isFinished', !finishedItem.isFinished);
    }
  }
}
</script>

<style>
* {
  box-sizing: border-box;
}

#app {
  background-color: #f0ecab;
  box-shadow: 0 0 10px rgba(0, 0, 0, .5);
  color: #2c3e50;
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  margin: 60px auto;
  max-width: 100%;
  padding: 20px;
  text-align: left;
  width: 800px;
}

#app h1 {
  text-align: center;
}
</style>
