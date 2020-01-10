<template>
  <div>
      <input type="text" class="todo-input"  placeholder="what needs to be done"  v-model="newTodo" v-on:keyup.enter="addTodo">
      <div v-for= "(todo, index) in todos" :key="todo.id" class="todo-item">
            <div>
                <div>{{todo.title}}</div>
                <input type="text" v-model="todo.title">
            </div>
            <div class="remove-item" @click="removeTodo(index)">
                &times; <!--Added a remove item x-->
            </div>
      </div>
  </div>
</template>

<script>
export default {
  name: 'todo-list',
  data () {
    return {
      newTodo: '',
      idForTodo:3,
      todos: [
        {
            'id': 1,
            'title': 'Finish Vue Screencast',
            'completed': false,
        },
        {
            'id': 2,
            'title': 'Take over world',
            'completed': false,
        }
      ]
    }
  },
  methods:{
      addTodo: function(){
          if(this.newTodo.trim().length==0){ //Check if input is empty
              return
          }
          this.todos.push({
              id: this.idForTodo,
              title: this.newTodo,
              completed: false,
          })
          this.newTodo='';
          this.idForTodo++;
      },
      removeTodo: function(index){
          this.todos.splice(index, 1)
      }
  }

}
</script>


<style lang="scss">
.todo-input {
    width: 100%;
    padding: 10px 18px;
    font-size: 18px;
    margin-bottom: 16px;
    &:focus {
        outline: 0px;
    }
}
.todo-item { //space between the created todoes
    margin-bottom: 12px;
    display: flex;
    align-items: center;
    justify-content: space-between;
}
.remove-item{ //styling for the remove item x called &times
    cursor: pointer;
    margin-left: 14px;
    &:hover {
        color: black;
    }
}
</style>
