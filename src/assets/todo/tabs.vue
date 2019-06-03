<template>
  <div class="helper">
    <span  class="left">{{ unFinshedTodoLength }} item left</span>
    <span class="tabs">
      <span
      v-for="state in states"
      :key="state.state"
      :class="[state, filter === state ? 'actived' : '']"
      @click="toggleState(state)"

      >
      {{ state }}
    </span>
    </span>
    
    <span class="clear">Clear complated</span>
  </div>
</template>
<script>
export default {
  data(){
    return {
      states: ['all', 'active', 'complated']
    }
  },
  props: {
    filter: {
      type: String,
      required: true
    },
    todos: {
      type: Array,
      required: true
    }
  },
  computed: {
    unFinshedTodoLength(){
      return this.todos.filter(todo => !todo.complated).length
    }
  },
  methods:{
    toggleState(state){
      this.$emit('toggle', state)
    }
  }

}
</script>

<style lang="stylus" scoped>
    .helper {
        font-weight 100
        display flex
        justify-content space-between
        padding 5px 0
        line-height 30px
        background-color #ffffff
        font-size 14px
        font-smoothing: antialiased;
    }
    .left, .clear, .tabs {
        padding 0 10px
        box-sizing border-box
    }
    .left, .clear {
        width 150px
    }
    .left {
        text-align left
    }
    .clear {
        text-align: right
        cursor pointer
    }
    .tabs {
        width 200px
        display flex
        justify-content space-around
        * {
            display inline-block
            padding 0 10px
            cursor pointer
            border 1px solid rgba(175, 47, 47, 0)
            &.actived {
                border-color rgba(175, 47, 47, 0.4)
                border-radius 5px
            }
        }
    }
</style>