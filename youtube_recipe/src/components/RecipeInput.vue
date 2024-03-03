<template>
  <div>
    <input
      type="text"
      v-model="newRecipe"
      placeholder="Type what you have to do"
      v-on:keypress.enter="addRecipe"
    />
    <span class="addContainer" v-on:click="addRecipe">
      <i class="addBtn fas fa-plus" aria-hidden="true"></i>
    </span>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newRecipe: ''
    }
  },
  methods: {
    addRecipe() {
      if (this.newRecipe !== '') {
        var value = this.newRecipe && this.newRecipe.trim()
        this.$emit('addRecipe', value) //App.vue에 있는 addRecipe 실행
        this.clearInput()
      }
    },
    clearInput() {
      this.newRecipe = ''
    }
  }
}
</script>

<style scoped>
input:focus {
  outline: none;
}
.inputBox {
  background: white;
  height: 50px;
  line-height: 50px;
  border-radius: 5px;
}
.inputBox input {
  border-style: none;
  font-size: 0.9rem;
}
.addContainer {
  background: linear-gradient(to right, #6478fb, #8763fb);
  display: inline-block;
  width: 3rem;
  border-radius: 0 5px 5px 0;
}
.addBtn {
  color: white;
  vertical-align: middle;
}
</style>