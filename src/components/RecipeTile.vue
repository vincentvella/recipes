<template>
  <div class="tile">
    <img :src=imageURL :width="250" :height="250"/>
    <div class="tile-content">
      <div class="tile-text">
        <h4>{{ name }}</h4>
      </div>
      <p>Time: {{ timers.reduce((acc, time) => acc += time, 0) }} minutes</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'RecipeTile',
  props: {
    name: {
      type: String,
      required: true,
    },
    imageURL: {
      type: String,
      required: true,
    },
    timers: {
      type: Array[String],
      required: true,
    }
  }
}
</script>

<style>
.tile {
  margin: 0 24px 24px 0;
  width: 250px;
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
  border-radius: 4px;
  transition: 0.3s;
  display: flex;
  flex-direction: column;
}

.tile-content {
  padding: 10px;
  position: relative;
  display: flex;
  flex: 1;
}

.tile-text {
  display: flex;
  flex: 1;
  padding-bottom: 8px;
}

.tile-content p {
  position: absolute;
  bottom: 0;
}

</style>