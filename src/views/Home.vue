<template>
  <div class="home">
    <h1>Recipes</h1>
    <RecipeList />
  </div>
</template>

<script>
import RecipeList from '@/components/RecipeList.vue';

export default {
  name: 'Home',
  components: {
    RecipeList,
  }
}
</script>
