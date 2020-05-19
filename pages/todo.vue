<template>
  <div class="center main-area">
    <h1>Todoリスト</h1>

    <div class="add-area">
      <input type="text" v-model="addTitle" />
      <button @click="onClickAdd">
        登録
      </button>
    </div>

    <hr/>

    <input type="checkbox" v-model="displayFlg" />
    完了したものを非表示にする
    <hr/>

    <div class="list-area">
      <div v-for="(task, index) in displayTasks" :key="index">
        <div :class="{'todo': true, 'finish': task.finishFlg}">
          <input type="checkbox" v-model="task.finishFlg">
          <span class="task-title">
            {{ task.title }}
          </span>
          <button class="task-right" @click="onClickDelete(index)">
            削除
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      addTitle: '',
      displayFlg: false,
      tasks: [{
        title: 'サンプル',
        finishFlg: false
      }]
    }
  },
  methods: {
    onClickAdd() {
      this.tasks.push({
        title: this.addTitle,
        finishFlg: false
      })
      this.addTitle = ''
    },
    onClickDelete(index) {
      this.tasks.splice(index, 1);
    }
  },
  computed: {
    displayTasks() {
      return this.tasks.filter(value => {
        if (!this.displayFlg) {
          // 全て表示
          return true
        }
        return !value.finishFlg
      })
    }
  }
}
</script>

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