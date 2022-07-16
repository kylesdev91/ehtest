<template>
  <div id="nav">
    <h2 style="margin-left: 5px">Kai Family Farm</h2>
    <img src="leaf.jpg" />
    <!-- <router-link :class="{ active: $route.name === 'Home' }" to="/"
      >Home</router-link
    > -->
    <!-- <i class="glyphicon glyphicon-cloud"></i> -->
    <!-- <router-link :class="{ active: $route.name === 'Cart' }" to="/cart"
      >Cart</router-link
    > -->
    <!-- <router-link to="/cart">Cart</router-link> -->
    <img src="shoppingcart.jpeg" />
  </div>
  <router-view />
</template>

<script>
export default {
  mounted() {
    this.$store.commit('updateCartFromLocalStorage');
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
}

html,
body {
  margin: 0;
  padding: 0;
  /* overflow-x: hidden; */
}

body {
  background-color: rgb(245, 245, 245);
}

#nav {
  /* padding: 5px; */
  display: flex;
  overflow: hidden;
  position: fixed;
  /* width: 100%; */
  /* height: 30px; */
  background-color: white;
  line-height: 10px;
  /* position: relative; */
  /* margin-bottom: 100; */
  top: 0;
  justify-content: space-between;
  width: 100%;

  a {
    font-weight: bold;
    color: darkgray;
    text-decoration: none;
    margin: 10px 10px;
    font-size: 1.25rem;

    &.active {
      color: #2c3e50;
    }
  }
}

.text-center {
  text-align: center;
}
</style>
