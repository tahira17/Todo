<template>
    <form @submit.prevent="addItemAndClear(todo)">
        <input v-model="todo" type ="text"/>
        <button>Add</button>
        

    </form>
</template>
<script> 
import {ref} from 'vue'
// import {useToDoListStore} from '../../src/stores/useToDoListStore'
import {useToDoListStore} from '@/stores/useToDoListStore'
export default{
    setup(){
        function addItemAndClear(item){
            if(item.length === 0){
                return
            }
            store.addTodo(item)
            todo.value=''
        }
        const todo= ref("")
        const store=useToDoListStore()
        return{
            todo,
            addItemAndClear
        }
     
    }
}
</script>

<style scoped>
form {
  margin-bottom: 15px;
}
input {
  margin-top: 25px;
  margin-bottom: 15px;
  height: 20px;
  width: 50%;
}
button {
  margin-left: 30px;
  background-color: #2f6089;
  padding: 5px 10px;
  border: none;
  border-radius: 5px;
  font-weight: 800;
  color: white;
  width: 15%;
}
.alert-div {
  min-height: 25px;
}
.alert {
  color: #d1495b;
  font-size: 1em;
  font-weight: 600;
}
</style>
Footer
© 2023 GitHub, Inc.
Footer navigation
