
<template>
  <div>
    <button v-show="false" class="tstbtn warning" v-on:click="count++">Click count: {{ count }}</button>
    <button class="addnew icon-paper-plane" @click="onAdd">+</button>
    <input type="text" placeholder="add todo.." autofocus 
      v-model="todoText"
      v-on:keyup.enter="onAdd" 
    />
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
input {
  width: auto;
  color: black;
}
</style>
