<template>
 
        <div v-for="todo in todoList" :key="todo.id">
            <div>
        <span :class="{ completed: todo.completed }">
            {{ todo.item }}
        </span>
        <span @click.stop="toggleCompleted(todo.id)">&#10004;</span>
        <span @click="deleteTodo(todo.id)">&#10060;</span>

    </div>
    </div>
</template>
<script>
import { useToDoListStore } from "../stores/useToDoListStore";
import { storeToRefs } from "pinia";
export default {
  setup() {
    const store = useToDoListStore();
    // storeToRefs lets todoList keep reactivity:
    const { todoList } = storeToRefs(store);

    const {toggleCompleted } = store
    const {deleteTodo} = store

    return { todoList , toggleCompleted , deleteTodo};
  },
};
</script>
<style scoped>
span {
  margin: 0 10px;
  cursor: pointer;
}
 .completed{
    text-decoration: line-through;
  }
  .list {
  display: flex;
  justify-content: center;
}
.item {
  display: flex;
  font-size: 1.5em;
  justify-content: space-between;
  width: 80vw;
  padding: 5px;
}
</style>
