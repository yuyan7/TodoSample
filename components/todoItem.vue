<template>
  <div :class="{'todo': true, 'finish': task.finishFlg, 'component': true}">
    <input type="checkbox" v-model="task.finishFlg">
    <span class="task-title">
      {{ task.title }}
    </span>
    <button class="task-right" @click="onClickDelete">
      削除
    </button>
  </div>
</template>

<script>
export default {
  props: {
    task: Object,
    index: Number
  },
  methods: {
    onClickDelete() {
      this.$emit('delete', this.index)
    }
  }
}
</script>

<style scoped>
.todo.component {
  background-color: aquamarine;
}
</style>
