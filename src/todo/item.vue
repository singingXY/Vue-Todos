<template>
  <div :class="['todo-item', todo.completed ? 'completed' : '']">
    <input type="checkbox" class="toggle" v-model="todo.completed" />
    <label>{{ todo.completed }}</label>
    <button class="destroy" @click="deleteTodo"></button>
  </div>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true
    }
  },
  methods: {
    deleteTodo () {}
  }
}
</script>

<style lang="less" scoped>
.todo-item {
  position: relative;
  background-color: #fff;
  font-size: 24px;
  border-bottom: 1px solid #0000000f;
  &:hover {
    .destroy:after {
      content: url('../assets/images/X.svg');
    }
  }
  label {
    white-space: pre-line;
    word-break: break-all;
    padding: 15px 60px 15px 15px;
    margin-left: 45px;
    display: block;
    line-height: 1.2;
    transition: color 0.4s;
  }
  &.completed {
    label {
      color: #d9d9d9;
      text-decoration: line-through;
    }
  }
}
.toggle {
  text-align: center;
  width: 28px;
  height: 28px;
  position: absolute;
  top: 0;
  bottom: 0;
  left: 10px;
  margin: auto 0;
  border: none;
  appearance: none;
  outline: none;
  &:after {
    content: url('../assets/images/unChecked.svg');
  }
  &:checked:after {
    content: url('../assets/images/checked.svg');
  }
}
.destroy {
  position: absolute;
  top: 0;
  bottom: 0;
  right: 10px;
  width: 32px;
  height: 32px;
  text-align: center;
  margin: auto 0 11px;
  padding: 0;
  font-size: 30px;
  color: #cc9a9a;
  transition: color 0.2s ease-out;
  background-color: transparent;
  border-width: 0;
  cursor: pointer;
  outline: none;
}
</style>
