<template>
  <ul class="todo-main">
    <my-item v-for="todo in todos" :key="todo.id" :todo="todo" @updateTodoObj="updateTodoObj" @deleteTodoObj="deleteTodoObj"></my-item>
  </ul>
</template>
  
  <script>
import MyItem from "./MyItem.vue";
export default {
  components: { MyItem },
  name: "MyList",
  props: ["todos"],
  data() {
    return {
        
    };
  },
  methods: {
    updateTodoObj(id, done) {
      this.$emit("updateTodoObj", id, done);
    },
    deleteTodoObj(id) {
      this.$emit("deleteTodoObj", id);
    },
  },
  
};
</script>
  
  <style scoped>
/*main*/
.todo-main {
  margin-left: 0px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding: 0px;
}

.todo-empty {
  height: 40px;
  line-height: 40px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding-left: 5px;
  margin-top: 10px;
}
</style>