<template>
  <div class="add">
    <h2>Add a Recipe</h2>
    <form id="sum">
      <div>
        <label for="name">Recipe Name</label><br/>
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
        <label for="steps">Steps</label><br />
        <div v-for="(step, index) in steps" :key="index" class="ingredient-inputs">
          <div>
            <label for="step.time">Time (min) </label><br />
            <input type="number" class="ingredient-input min" v-model="step.time" />
          </div>
          <div>
            <label for="step.step">Step</label><br />
            <textarea class="ingredient-input" v-model="step.step" />
          </div>
          <div @click="deleteStep(index, $event)" class="del">
            🗑
          </div>
        </div>
      </div>
      <button @click="addStep" type="button" class="btn inv">
          + Add Step
      </button>
      <div>
        <label for="name">Image URL</label><br/>
        <input type="text" class="form-control" v-model="imageURL" />
      </div>
      <div>
        <label for="name">Original URL</label><br/>
        <input type="text" class="form-control" v-model="originalURL" />
      </div>
      <button @click="addRecipe" type="button" class="btn">
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
          steps: [{
            time: 0,
            step: '',
          }],
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
        },
        addStep: function () {
          this.steps.push({ time: 0, step: '' })
        },
        deleteStep: function (indexToDelete) {
          if (indexToDelete === 0 && this.steps.length === 1) {
            this.steps = [{time: 0, step: ''}];
          } else {
            this.steps.splice(indexToDelete, 1);
          }
        },
        addRecipe: function () {
          console.log('TODO: Add Recipe to JSON w/ fs', 'RECIPE:', {
            name: this.name,
            ingredients: this.ingredients,
            imageUrl: this.imageURL,
            originalURL: this.originalURL,
            ...this.steps.reduce((acc, {time, step}) => {
              acc.steps.push(step);
              acc.timers.push(time);
              return acc;
             }, {steps: [], timers: []})
          })
        }
    }
}
</script>
<style scoped>
    label {
      font-size: 24px;
    }
    .form-control {
        margin-bottom: 15px;
        width: 400px;
        font-size: 18px;
    }
    .ingredient-inputs {
      width: 400px;
      display: flex;
      flex-direction: row;
    }
    .ingredient-input {
      font-size: 18px;
      margin-bottom: 15px;
      flex: 1;
      width: 250px;
      max-width: 250px;
      min-width: 250px;
    }
    .min {
      width: 100px;
      margin-right: 15px;
      min-width: 0px;
    }
    .btn {
      background-color: #35495e;
      padding: 10px 20px;
      width: 400px;
      color: #fff;
      border-width: 0px;
      border-radius: 5px;
      margin-bottom: 16px;
    }
    .del {
      align-self: center;
      padding-left: 8px;
      padding-top: 16px;
    }
    .inv {
      padding: 8px 10px;
      color: #35495e;
      border-color: #35495e;
      background-color: #fff;
      border-width: 1px;
    }
</style>