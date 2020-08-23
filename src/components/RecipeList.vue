<template>
  <RecipeTile v-for="recipe in recipes" v-bind:key="recipe.name" v-bind="recipe" />
</template>

<script>
import Recipes from '@/data/recipes.json';
import RecipeTile from '@/components/RecipeTile.vue';

export default {
  name: 'RecipeList',
  components: {
    RecipeTile,
  },
  data () {
    return {
      recipes: Recipes.list,
    }
  }
}
</script>