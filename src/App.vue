<template>
  <div id="app">
   <div class="container grid-xs py-2">
    <img src="@/assets/logo.png" alt="logo" class="img-responsive image-logo">
    <form @submit.prevent="addTodo">
      <div class="input-group">
        <input v-model="todo.description" type="text" class="form-input" placeholder="Novo todo">
        <button class="btn btn-primary input-group-btn">Adicionar</button>
      </div>
    </form>
      <div class="todo-list">
        <Todo v-for="t in todos" :key="t.id" @toggle="toggleTodo" @remove="rmTodo" :todo="t"/> 
      </div>
   </div>
  </div>
</template>

<script> 
import Todo from './components/Todo' 
export default {
  name: 'App',
  components:{
    Todo
  },
  data(){
    return{
      todos:[],
      todo:{checked:false}
    }
  },
  methods:{
    addTodo(){
      this.todo.id = Date.now();
      this.todos.push(this.todo);
      this.todo = {checked:false};
    },
    toggleTodo(todo){
      const index = this.todos.findIndex(item=>item.id === todo.id);
      if(index > -1){
        const checked = !this.todos[index].checked;
        this.$set(this.todos,index,{...this.todos[index],checked})
        
      }
    },
      rmTodo(todo){
        const index = this.todos.findIndex(item=>item.id === todo.id);
        if(index > -1){
          this.$delete(this.todos,index);
        }
      }
  }
}
</script>

<style scoped>
.image-logo{
  max-width: 150px;
  margin: 0 auto;
  padding: 10px;
}
.todo-list{
  padding-top: 2rem;
}
</style>

