
<template>
  <div id="root">
    <br />
    <button v-on:click="show_extra = !show_extra" > {{ msg }}  </button>
    <!-- <div v-if="show_extra"> Add a new todo </div> -->
    <div v-show="show_extra"> <add-todo-comp v-on:add="addTodo" /> </div>

    <br />

<!-- the list itself -->
    <ol>
      <li v-for="item in todo_list" :key="item.text">
        <item-comp :text="item.text" :done="item.done" />
      </li>
    </ol>  

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
    }
  }
}

</script>

<!------------------------------------------------------------------------------------------->

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
/* * {
  background: black;
  color: greenyellow;
  padding: 10px;
}
#root {
  margin: 0 auto;
  width: 50%;
  padding: 40px;
}
button {
  background: darkslateblue;
} */
#root {
  background: rgb(26, 26, 26);
  color:cyan;
  margin: 0 auto;
  width: 50%;
  padding: 40px;
}
ol {
  display: inline-block;
  text-align:left;
}
</style>
