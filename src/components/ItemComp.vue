<template>
<span :style="{'text-decoration': done ? 'line-through' : 'none'}" @click="done=!done"> 
  {{text}} 
</span>
</template>

<script>
export default {
  name: 'ItemComp',
  props: {
    text: String,
    done: Boolean,
  }
}
</script>

<style>
span {
  cursor: pointer;
  color: cyan;
}
</style>