<template>
  <div class="add">
    <h1>{{recipe.name}}</h1>
    <img :src=recipe.imageURL :width="250" :height="250"/>
    <h3>Ingredients</h3>
    <ul v-for="ingredient in recipe.ingredients" v-bind:key="ingredient.name">
      <li>{{ingredient.quantity}} of {{ingredient.name}}</li>
    </ul>
    <h3>Steps</h3>
    <div v-for="(step, index) in recipe.steps" v-bind:key="step">
      <div>{{index + 1}}. {{step}}</div>
    </div>
  </div>
</template>

<script>
import Recipes from '@/data/recipes.json';

export default {
  name: 'Recipe',
  data: function () {
    return {
      recipe: Recipes.list.find(({id}) => this.$route.params.id == id),
    }
  }
}
</script>