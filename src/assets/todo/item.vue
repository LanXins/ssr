<template>
  <div>
    <div :class="['todo-item', todo.completed ? 'complated' : '']">
      <input type="checkbox" class="toggle" v-model="todo.complated">
      <label>{{ todo.content }}</label>
      <button class="destory" @click="deleteTodo(todo.id)">X</button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    todo: {
      Object,
      required: true
    }
  },
  methods: {
    deleteTodo(){}
  }
};
</script>

<style scoped lang="stylus">
.todo-item {
  position: relative;
  background-color: #fff;
  font-size: 24px;
  border-bottom: 1px solid rgba(0, 0, 0, 0.06);

  &:hover .destory {
    font-size: 30px;
  }

  label {
    white-space: pre-line;
    word-break: break-all;
    padding: 15px 60px 15px 15px;
    margin-left: 45px;
    display: block;
    line-height: 1.2;
    transition: color 0.4s;
    padding-left: 32px;
    text-align: left;
  }

  &.completed {
    label {
      color: #d9d9d9;
      text-decoration: line-through;
    }
  }
}

.destory {
  position: absolute;
  top: 0;
  right: 10px;
  bottom: 0;
  width: 40px;
  height: 40px;
  margin: auto 0;
  font-size: 0;
  color: #cc9a9a;
  margin-bottom: 11px;
  transition: color 0.2s ease-out;
  background-color: transparent;
  appearance: none;
  border-width: 0;
  cursor: pointer;
  outline: none;
}

.toggle {
  text-align: center;
  width: 40px;
  height: 40px;
  line-height: 40px;
  position: absolute;
  top: 0;
  bottom: 0;
  margin: auto 0;
  border: none;
  appearance: none;
  outline: none;
  padding-left: 5px;
  cursor: pointer;
  left: 21px;

  &:after {
    content: url('../images/round.svg');
  }

  &:checked:after {
    content: url('../images/done.svg');
  }
}
</style>