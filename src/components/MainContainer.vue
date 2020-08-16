
<template>
  <div id="root">
    <br />
    <button v-on:click="show_extra = !show_extra" > {{ msg }}  </button>
    <!-- <div v-if="show_extra"> Add a new todo </div> -->
    <div v-show="show_extra"> <add-todo-comp v-on:add="addTodo" /> </div>

    <br />
<!-- the list itself -->
    <!-- <ol>
      <li v-for="item in todo_list" :key="item.text">
        <item-comp :text="item.text" :done="item.done" />
      </li>
    </ol>   -->

  
  

<div class="card border-secondary mb-3 mx-auto w-75 mw-50" style="max-width:50em">
  <!-- <div class="card-header">
    <div v-show="show_extra"> <add-todo-comp v-on:add="addTodo" /> </div>
  </div> -->
  <div class="card-body">
    <h4 class="card-title">
      <div v-show="show_extra"> <add-todo-comp v-on:add="addTodo" /> </div>
    </h4>
    <p class="card-text">
      <ul class="list-group ">

        <item-comp :text="item.text" :done="item.done" :uid="index"
          v-for="(item,index) in todo_list" :key="item.text"
          @swiped="removeTodo(index)"
        />

        <!-- <li class="list-group-item d-flex justify-content-between align-items-center "
          v-for="(item,index) in todo_list" :key="item.text"
          v-touch-class="'touched-element'"
          v-touch:start="swipeStart"
          v-touch:swipe="swipeTodo(item.text)"
        >
          <item-comp :text="item.text" :done="item.done" :uid="index" /> -->
          
       
      </ul>
    </p>
  </div>
</div>

  </div>
</template>

<!------------------------------------------------------------------------------------------->

<script>
import AddTodoComp from './AddTodoComp.vue';
import ItemComp from './ItemComp.vue';

export default {
  name: 'MainContainer', 
  components: { 
    AddTodoComp,
    ItemComp,
  },
  props: {
    msg: String,
    name: String,

    // example for a more complex validation of a prop object
    count: {
      type: Number,
      default: 0,
      required: false,
      validator: (value) => value >= 0
    }
  },

  data: ()=>{ return {
    show_extra: Boolean,
    todo_list:  [
      { text: "first item", done: true},
      { text: "second item", done: false},
      { text: "third item", done: false},
    ],
  }},

  methods : { 
    toggleshow_extra() {
      this.data.show_extra = !this.data.show_extra;
    },
    addTodo(str) {
      this.todo_list.push( {text: str, done:false} );
    },
    removeTodo(index) {
      this.todo_list.splice(index, 1);
    }
  }
}

</script>

<!------------------------------------------------------------------------------------------->

<!-- Add "scoped" attribute to limit CSS to this component only -->

<style scoped>
/* #root {
  background: rgb(26, 26, 26);
  color:cyan;
  margin: 0 auto;
  padding: 20px;
  width: 50%;
  height: 90%;
  min-height: 300px;
  max-width: 600px;
}
ol {
  display: inline-block;
  text-align:left;
} */
</style>
