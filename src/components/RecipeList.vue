<template>
  <div class="list">
    <RecipeTile v-for="recipe in recipes" v-bind:key="recipe.name" v-bind="recipe" />
  </div>
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

<style scoped>
.list {
  display: flex;
  flex-wrap: wrap;
  height: 400px;
  align-content: space-between;
}
</style>