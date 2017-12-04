<template>
    <div>
        <ul>
            <li>To do A</li>
            <li>To do B</li>
            <li>To do C</li>
            <li>{{ msg }}</li>
        </ul>
        <p>Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}</p>
        <p>Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}</p>
 
<todo  v-on:delete-todo="deleteTodo" v-for="todo in todos" v-bind:todo="todo"></todo>
    <div class='ui centered card'>
      
    <div class="content" v-show="!isEditing">
      <div class='header'>
          {{ todo.title }}
      </div>
      <div class='meta'>
          {{ todo.project }}
      </div>
      <div class='extra content'>
    <span class='right floated edit icon' v-on:click="showForm()">
      <i class='edit icon'></i>
    </span>
    <i class="trash icon"></i>
      </div>
    </div>
    
    <div class="content" v-show="isEditing">
      <div class='ui form'>
        <div class='field'>
          <label>Title</label>
          <input type='text' v-model="todo.title" >
        </div>
        <div class='field'>
          <label>Project</label>
          <input type='text' v-model="todo.project" >
        </div>
        <div class='ui two button attached buttons'>
          <button class='ui basic blue button' v-on:click="hideForm">
            Close X
          </button>
        </div>
      </div>
    </div>
    <div class='ui bottom attached green basic button' v-show="!isEditing &&todo.done" disabled>
        Completed
    </div>
    <div class='ui bottom attached red basic button' v-show="!isEditing && !todo.done">
        Pending
    </div>
  </div>
    </div>
</template>

<script type="text/javascript">

// import Todo from './Todo';

export default {
  name: 'Hello',
//   props: ['todos'],
  components: {
    //   Todo,
  },
  props:["todo"],
  data () {
    return {
      msg: 'This is a directive',
      isEditing: false,
      methods:{
        showForm() {
        this.isEditing = true;
        },
        hideForm() {
        this.isEditing = false;
        },
      },
      todos:[{
          title: 'first to do', 
          project: 'first project', 
          done: true,
      },
      {
          title: 'second to do', 
          project: 'second project', 
          done: false,
      },
      {
          title: 'third to do', 
          project: 'third project', 
          done: false,
      },
      ]
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b9;
}
</style>
