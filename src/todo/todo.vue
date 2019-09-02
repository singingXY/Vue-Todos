<template>
  <div class="real-app">
    <input
      type="text"
      class="add-input"
      autofocus
      placeholder="接下来要做什么？"
      @keyup.enter="addTodo"
    />
    <Item :todo="todo"></Item>
  </div>
</template>

<script>
import Item from './item'
export default {
  data () {
    return {
      todo: {
        id: 0,
        content: 'this is todo',
        completed: false
      }
    }
  },
  components: {
    Item
  },
  methods: {
    addTodo () {}
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
