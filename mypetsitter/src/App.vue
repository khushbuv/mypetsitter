<template>
  <div id="app">
    <nav class="navigation">
      <div class="navigation__logo">
        Twotter
      </div>
      <div class="navigation__user">
        {{ user.username }}
      </div>
    </nav>
    <router-view/>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      user: {
        username: 'Khushbub84'
      }
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  min-height: 100vh;
  background-color: #F3F5FA;


  .navigation {
    background-color: deeppink;
    align-items: center;
    justify-content: space-between;
    padding: 10px 5%;
    background-color: deeppink;
    color: white;

    .navigation__logo {
      font-weight: bold;
      font-size: 24px;
      //text-align: left;
    }

    .navigation__user {
      font-weight: bold;
      text-align: right;
    }
  }
}


</style>
