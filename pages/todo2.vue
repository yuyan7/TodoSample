<template>
  <div class="center main-area component">
    <h1>Todoリスト</h1>

    <add-area @add="onAdd" />

    <hr />

    <div class="list-area">
      <div v-for="(task, index) in tasks" :key="index">
        <todo-item :task="task" @delete="onDelete" />
      </div>
    </div>
  </div>
</template>

<script>
import addArea from '~/components/addArea'
import todoItem from '~/components/todoItem'

export default {
  components: {
    addArea,
    todoItem
  },
  data() {
    return {
      tasks: [{
        title: 'サンプル',
        finishFlg: false
      }]
    }
  },
  methods: {
    onAdd(task) {
      this.tasks.push(task);
    },
    onDelete(index) {
      this.tasks.splice(index, 1)
    }
  }
}
</script>

<style scoped>
.main-area.component {
  background-color: skyblue;
}
</style>

<style>
.main-area {
  width: 700px;
}

.center {
  margin: auto;
  text-align: center;
}

.list-area {
  margin: auto;
  text-align: center;
  width: 500px;
}

.todo {
  border: solid 1px;
  padding: 10px;
  text-align: left;
}

.task-right {
  float: right;
}

.task-left {
  float: left;
}

.finish {
  color: white;
  background-color: gray;
}
</style>
