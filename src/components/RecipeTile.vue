<template>
  <div>
    <h2>{{ name }}</h2>
  </div>
</template>

<script>
export default {
  name: 'RecipeTile',
  props: {
    name: {
      type: String,
      required: true,
    }
  }
}
</script>