<template>
  <div class="container-board">
    <div class="columns">
      <div class="column col-5">
        <div class="panel">
          <div class="panel-header">
            <div class="panel-title">To do</div>
          </div>
          <div class="panel-body">
            <Todo v-for="todo in uncheckeds" :todo="todo" @remove="removeTodo" @toggle="toggleTodo" :key="todo.id"/>
          </div>
          <div class="panel-footer">
            <button v-if="uncheckeds.length>0" class="btn btn-link float-right" @click="checkAll">Concluir tudo</button>
          </div>
        </div>
      </div>
      <div class="column col-5">
        <div class="panel">
          <div class="panel-header">
            <div class="panel-title">Done</div>
          </div>
          <div class="panel-body">
           <Todo v-for="todo in checkeds" :todo="todo" @remove="removeTodo" @toggle="toggleTodo" :key="todo.id"/>
          </div>
          <div class="panel-footer">
            <button v-if="checkeds.length>0" class="btn btn-link float-right  text-error" @click="removeAllCheckeds">Remover todos</button>
            <button v-if="checkeds.length>0" class="btn btn-link float-right" @click="uncheckAll">Desmarcar todos</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Todo from '@/components/Todo';
import {mapGetters,mapActions} from 'vuex';
export default {
    components:{
        Todo
    },
    computed:{
        ...mapGetters(['uncheckeds','checkeds'])
    },
    methods:{
        ...mapActions(['toggleTodo','removeTodo','checkAll','uncheckAll','removeAllCheckeds'])
    }
};
</script>

<style scoped>
.container-board {
  height: calc(100vh - 100px);
  padding: 10px;
}
.columns {
  height: 100%;
}

.columns .column .panel {
  height: 100%;
  border: 0;
  box-shadow: 0 0.25rem 1rem rgba(48,55,66, 0.15);
}
</style>