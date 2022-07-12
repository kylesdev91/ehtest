<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
  </div>
</template>

<script>
// @ is an alias to /src
import items from '../data/items.js';

export default {
  name: 'Home',
  components: {},
  data() {
    return {
      items: items,
    };
  },
};
</script>
