
<template>
  <div>

<div class="form-group ">
  <!-- <label class="form-control-label " for="addTextbox">Add Todo</label> -->
<!-- <br /> -->

  <div class="input-group add-wrapper " >
    <button type="button" @click="onAdd" 
      class="btn btn-outline-success addnew fa fa-plus" ></button>
    <div class="col-8">
      <input type="text" placeholder="add todo.." class="form-control" id="addTextbox"
        autofocus 
        v-model="todoText"
        v-on:keyup.enter="onAdd" 
      >
    </div>
  </div>
  
</div>

<!-- 
    <button v-show="false" class="tstbtn warning" v-on:click="count++">Click count: {{ count }}</button>
    <div class="add-wrapper">
      <button class="addnew fa fa-plus" @click="onAdd"></button>
      <input type="text" placeholder="add todo.." autofocus 
        v-model="todoText"
        v-on:keyup.enter="onAdd" 
      />
    </div> -->
  </div>
</template>

<!------------------------------------------------------------------------------------------->

<script>
export default {
  name: "AddTodoComp",
  data: () => {
    return {
      count: 0,
      todoText: ""
    };
  },
  methods: {
    onAdd() {
      this.$emit("add", this.todoText);
      // clear text after we send the add signal
      this.todoText = "";
    }
  }
};
</script>

<!------------------------------------------------------------------------------------------->

<style scoped>
.btn {
  /* necesary for some reason bootstrap changes it so it offset slightly */
  font-size: 1rem; 
}
/* input {
  width: auto;
  color: black;
}
.addnew {
  height:36px;
} */
</style>
