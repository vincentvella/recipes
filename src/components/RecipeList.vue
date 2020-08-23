<template>
  <div v-for="recipe in recipes" :key="recipe.name">
    <h2>{{recipe.name}}</h2>
  </div>
</template>

<script>
import Recipes from '@/data/recipes.json';

export default {
  name: 'RecipeList',
  data () {
    return {
      recipes: Recipes.list,
    }
  }
}
</script>