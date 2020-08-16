<template>
<!-- <span :style="{'text-decoration': done ? 'line-through' : 'none'}" @click="done=!done">  -->
<li class="list-group-item d-flex justify-content-between align-items-center "
  v-bind:class="{'swiping-element': swiping}"
          v-touch-class="'touched-element'"
          v-touch:start="swipeStart"
          v-touch:end="swipeEnd"
          v-touch:swipe="swipeTodo">
<!-- form-group -->

  <div class=" "> 
    <div class="form-check custom-checkbox">              
      <input type="checkbox" class="custom-control-input" 
        :id="getSUID()" 
        v-model="done"
      >
      <label class="custom-control-label noselect" 
        :for="getSUID()"
        :style="{'text-decoration': done ? 'line-through' : 'none'}">
          {{text}}
      </label>
    </div>
  </div>

  <!-- <a href="#" class="badge badge-primary badge-pill badge-danger">X</a> -->

<!-- </span> -->

</li>


</template>

<script>
export default {
  name: 'ItemComp',
  props: {
    uid: Number,
    text: String,
    done: Boolean,
  },

  data: ()=>{ return {
    swiping: false,
  }},

  methods: {
    getSUID() { return "checkbox"+this.uid; },
    swipeTodo() {
      // alert("hi "+this.text);
      // initiate callback to parent element to remove this item
      this.$emit('swiped', this);
    },
    swipeStart() {
      console.log("swipe start: "+this.text );
      //this.msg += "X";
      this.swiping = true;
    },
    swipeEnd() {
      this.swiping = false;
    }
  }
}
</script>

<style>
.touched-element {
  background-color: #3f3f3f;
  border-left: 5px solid #254996;
  /* this is a "hack" so the text wont move because of the border increase in size */
  padding-left: 16px;
}
.swiping-element {
  background-color: blueviolet;
}
span {
  cursor: pointer;
  color: cyan;
}

/* so text isnt selectable as we swipe */
.noselect {
  -webkit-touch-callout: none; /* iOS Safari */
    -webkit-user-select: none; /* Safari */
     -khtml-user-select: none; /* Konqueror HTML */
       -moz-user-select: none; /* Firefox */
        -ms-user-select: none; /* Internet Explorer/Edge */
            user-select: none; /* Non-prefixed version, currently
                                  supported by Chrome and Opera */
}
</style>