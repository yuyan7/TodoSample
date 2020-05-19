<template>
  <div class="add-area component">
    <input type="text" v-model="addTitle" />
    <button @click="onClickAdd">
      登録
    </button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      addTitle: ''
    }
  },
  methods: {
    onClickAdd() {
      const task = {
        title: this.addTitle,
        finishFlg: false
      }
      this.$emit('add', task)
      this.addTitle = ''
    }
  }
}
</script>

<style scoped>
.add-area.component {
  background-color: khaki;
}
</style>