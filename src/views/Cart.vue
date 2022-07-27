<template>
  <div>
    <button @click="sendEmail">Email</button>
    <div>
      <a v-if="userInfo" :href="`/.auth/logout`"><button>Logout</button></a>
      <a v-if="!userInfo" :href="`/.auth/login/aad`"><button>Login</button></a>
      <div class="user" v-if="userInfo">
        <p>Welcome</p>
        <p>{{ userInfo.userDetails }}</p>
      </div>
    </div>
  </div>
  <h2>{{ product.id }}</h2>
  <h2>{{ product.name }}</h2>
</template>

<script>
import items from '../data/items';
import axios from 'axios';
export default {
  data() {
    return {
      items: items,
      userInfo: {
        type: Object,
        default() {},
      },
    };
  },
  computed: {
    products() {
      return this.$store.getters.cartItems;
    },
  },

  props: ['product'],
  async created() {
    this.userInfo = await this.getUserInfo();
  },
  methods: {
    sendEmail() {
      console.log(this.userInfo.userDetails);
      var content = this.items.reduce(function (a, b) {
        return a + '<tr><td>' + b.id + '</a></td><td>' + b.name + '</td></tr>';
      }, '');
      var formData = {
        emailSubject: 'Online Order',
        emailBody: content,
        orderTotal: 10,
        emailAddress: this.userInfo.userDetails,
      };
      axios.post('/api/sendemail', formData).then((response) => {
        console.log(response);
      });
    },
    login() {
      this.$router.push('/.auth/login/aad');
    },
    async getUserInfo() {
      try {
        const response = await fetch('/.auth/me');
        const payload = await response.json();
        const { clientPrincipal } = payload;
        return clientPrincipal;
      } catch (error) {
        console.error('No profile could be found');
        return undefined;
      }
    },
  },
};
</script>
