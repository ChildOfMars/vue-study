<template>
  <div class="todo-footer" v-show="todos.length">
    <label>
      <input type="checkbox" :checked="isAllDone" @change="allDone" />
    </label>
    <span> <span>已完成{{ doneCount }}</span> / 全部{{ todos.length }} </span>
    <button class="btn btn-danger" @click="clearDone">清除已完成任务</button>
  </div>
</template>

<script>
export default {
  name: "MyFooter",
  props: ["todos"],
  data() {
    return {
    };
  },
  computed:{
    doneCount(){
      return this.todos.reduce((pre, todo) => pre + (todo.done ? 1 : 0), 0)
    },
    isAllDone(){
      return (this.todos.length === this.doneCount && this.todos.length > 0)
    }
  },
  methods: {
    allDone() {
      console.log(this.isAllDone);
      this.$emit("allDone", !this.isAllDone);
    },
    clearDone() {
      if(window.confirm("确定清除已完成任务吗？")){
        this.$emit("clearDone");
      }
    },
  },
};
</script>

<style scoped>
/*footer*/
.todo-footer {
  height: 40px;
  line-height: 40px;
  padding-left: 6px;
  margin-top: 5px;
}

.todo-footer label {
  display: inline-block;
  margin-right: 20px;
  cursor: pointer;
}

.todo-footer label input {
  position: relative;
  top: -1px;
  vertical-align: middle;
  margin-right: 5px;
}

.todo-footer button {
  float: right;
  margin-top: 5px;
}
</style>