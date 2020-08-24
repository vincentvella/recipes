<template>
  <div class="add">
    <h2>Add a Recipe</h2>
    <form id="sum">
      <div>
        <label for="name">Name</label><br/>
        <input type="text" class="form-control" v-model="name" />
      </div>
      <div>
        <label for="ingredients">Ingredients</label><br />
        <div v-for="(ingredient, index) in ingredients" :key="index" class="ingredient-inputs">
          <div>
            <label for="ingredient.quantity">Quantity</label><br />
            <input type="text" class="ingredient-input min" v-model="ingredient.quantity" />
          </div>
          <div>
            <label for="ingredient.name">Name</label><br />
            <input type="text" class="ingredient-input" v-model="ingredient.name" />
          </div>
          <div @click="deleteIngredient(index, $event)" class="del">
            🗑
          </div>
        </div>
      </div>
      <button @click="addIngredient" type="button" class="btn inv">
          + Add Ingredient
      </button>
      <div>
        <label for="name">Image URL</label><br/>
        <input type="text" class="form-control" v-model="imageURL" />
      </div>
      <div>
        <label for="name">Original URL</label><br/>
        <input type="text" class="form-control" v-model="originalURL" />
      </div>
      <button @click="addNumbers" type="button" class="btn">
          Add Recipe
      </button>
    </form>
  </div>
</template>
<script>
export default {
    name: 'Add',
    data() {
        return {
          name: '',
          ingredients: [{
            name: '',
            quantity: '',
          }],
          steps: [''],
          timers: [0],
          imageURL: undefined,
          originalURL: undefined,
        };
    },
    methods: {
        addIngredient: function () {
          this.ingredients.push({name: '', quantity: ''});
        },
        deleteIngredient: function (indexToDelete) {
          if (indexToDelete === 0 && this.ingredients.length === 1) {
            this.ingredients = [{name: '', quantity: ''}];
          } else {
            this.ingredients.splice(indexToDelete, 1);
          }
        }
    }
}
</script>
<style scoped>
    .add {
      width: 300px;
    }
    .form-control {
        margin-bottom: 15px;
        width: 300px;
    }
    .ingredient-inputs {
      width: 300px;
      display: flex;
      flex-direction: row;
    }
    .ingredient-input {
      margin-bottom: 15px;
      flex: 1;
      width: 175px;
    }
    .min {
      width: 100px;
      margin-right: 15px;
    }
    .btn {
      background-color: #35495e;
      padding: 10px 20px;
      width: 300px;
      color: #fff;
      border-width: 0px;
      border-radius: 5px;
      margin-bottom: 16px;
    }
    .del {
      align-self: center;
      padding-left: 8px;
      padding-top: 4px;
    }
    .inv {
      padding: 8px 10px;
      color: #35495e;
      border-color: #35495e;
      background-color: #fff;
      border-width: 1px;
    }
</style>