<template>
  <div id="app">
    <div id="nav">
      <div id="nav-content">
        <h2>VueMyRecipes</h2>
        <router-link to="/">Home</router-link>
        <router-link to="/add">Add</router-link>
      </div>
    </div>
    <div id="nav-view">
      <router-view/>
    </div>
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

#nav {
  background-color: #42b983;
  margin: -25px -10px;
  padding: 20px 15px 10px 15px;
}

#nav h2 {
  padding: 0 20px 0 10px;
}

#nav-content {
  display: inline-flex;
  align-items: center;
}

#nav a {
  font-weight: bold;
  color: #ffffff;
  padding: 10px;
}

#nav-view {
  padding: 15px
}

body {
  overflow-x: hidden;
}

</style>
