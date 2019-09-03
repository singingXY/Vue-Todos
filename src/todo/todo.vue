<template>
  <div class="real-app">
    <input
      type="text"
      class="add-input"
      autofocus
      placeholder="接下来要做什么？"
      @keyup.enter="addTodo"
    />
    <Item
      :todo="todo"
      v-for="todo in filteredTodos"
      :key="todo.id"
      @del="deleteTodo"
    />
    <tabs
      :filter="filter"
      :todos="todos"
      @toggle="toggleFilter"
    />
  </div>
</template>

<script>
import Item from './item'
import Tabs from './tabs'
let id = 0
export default {
  data () {
    return {
      todos: [],
      filter: 'all'
    }
  },
  components: {
    Item,
    Tabs
  },
  computed: {
    filteredTodos () {
      if (this.filter === 'all') {
        return this.todos
      }
      const completed = this.filter === 'completed'
      // 目的是把字符串转为一个true或fault的状态
      // filter返回true则显示，返回fault则不显示
      return this.todos.filter(
        todo => completed === todo.completed
      )
    }
  },
  methods: {
    addTodo (e) {
      this.todos.unshift({
        id: id++,
        content: e.target.value.trim(),
        completed: false
      })
      e.target.value = ''
    },
    deleteTodo (id) {
      this.todos.splice(
        this.todos.findIndex(todo => todo.id === id),
        1
      )
    },
    toggleFilter (state) {
      this.filter = state
    }
  }
}
</script>

<style lang="less" scoped>
.real-app {
  width: 600px;
  margin: 0 auto;
  box-shadow: 0 0 5px #cbcbcb;
}
.add-input {
  box-sizing: border-box;
  position: relative;
  width: 100%;
  font-size: 24px;
  line-height: 1.4;
  outline: none;
  padding: 6px;
  border: 0;
  padding: 16px 16px 16px 60px;
}
</style>
