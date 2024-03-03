<template>
  <div id="app">
    <RecipeHeader></RecipeHeader>
    <RecipeInput v-on:addRecipe="addRecipe"></RecipeInput>
    <RecipeList v-bind:propsdata="recipeItems"></RecipeList>
    <RecipeFooter v-on:removeAll="clearAll"></RecipeFooter>
  </div>
</template>

<script>
import RecipeHeader from './components/RecipeHeader.vue'
import RecipeInput from './components/RecipeInput.vue'
import RecipeList from './components/RecipeList.vue'
import RecipeFooter from './components/RecipeFooter.vue'

export default {
  data() {
    return {
      recipeItems: []
    }
  },
  created() {
    if (localStorage.length > 0) {
      for (var i = 0; i < localStorage.length; i++) {
        this.recipeItems.push(localStorage.key(i))
      }
    }
  },

  methods: {
    addRecipe(recipeItem) {
      localStorage.setItem(recipeItem, recipeItem)
      this.recipeItems.push(recipeItem) //RecipeInput과 연동
    },
    clearAll() {
      localStorage.clear()
      this.recipeItems = []
    }
  },

  components: {
    RecipeHeader: RecipeHeader,
    RecipeInput: RecipeInput,
    RecipeList: RecipeList,
    RecipeFooter: RecipeFooter
  }
}
</script>

<style>
body {
  text-align: center;
  background-color: #f6f6f8;
}
input {
  border-style: groove;
  width: 200px;
}
button {
  border-style: groove;
}
.shadow {
  box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03);
}
</style>