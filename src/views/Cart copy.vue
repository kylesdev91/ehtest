<template>
  <div style="margin-top: 35px; height: 2000px">
    <CartItemCard
      v-for="product in products"
      :key="product.id"
      :product="product"
    />
    <CartSummaryPaymentCard :getUser="getUserName" />
    <div>
      <div class="user" v-if="userInfo">
        <p>Welcome, {{ userInfo.userDetails }}</p>
      </div>
      <a v-if="userInfo" :href="`/.auth/logout`"
        ><button class="logout">Logout</button></a
      >
      <a v-if="!userInfo" :href="`/.auth/login/aad`"
        ><button class="login">Login</button></a
      >
      <button class="email" @click="sendEmail">Submit</button>
    </div>
  </div>
</template>

<script>
import CartItemCard from '../components/cart/CartItemCard.vue';
import CartSummaryPaymentCard from '../components/cart/CartSummaryPaymentCard.vue';
// import items from '../data/items';
import axios from 'axios';
export default {
  components: {
    CartItemCard,
    CartSummaryPaymentCard,
  },
  data() {
    return {
      name: '',
      // items: items,
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
      // var content = this.items.reduce(function (a, b) {
      var content = this.products.reduce(function (a, b) {
        return (
          a +
          '<tr><td>' +
          b.name +
          '</a></td><td style="text-align:center">' +
          b.quantity +
          '</td></td>'
        );
      }, '');
      var formData = {
        emailSubject: 'Online Order',
        emailBody: content,
        orderTotal: this.name,
        emailAddress: this.userInfo.userDetails,
      };
      axios.post('/api/sendemail', formData).then((response) => {
        console.log(response);
      });
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
    getUserName(name) {
      console.log(name);
      this.name = name;
    },
  },
};
</script>

<style lang="scss">
.login {
  background-color: green;
  /* font-weight: bold; */
  padding: 10px;
  /* width: 15%; */
  color: white;
  font-size: 20px;
  margin-left: 150px;
  width: 87px;
  /* width: 200px; */
  /* margin-left: 10px; */
  /* height: 100%; */

  /* position: relative; */
  /* margin: auto; */
}

.logout {
  background-color: green;
  /* font-weight: bold; */
  padding: 10px;
  /* width: 15%; */
  color: white;
  font-size: 20px;
  margin-left: 150px;
  width: 87px;
  /* width: 200px; */
  /* margin-left: 10px; */
  /* height: 100%; */

  /* position: relative; */
  /* margin: auto; */
}

.user {
  background-color: none;
  font-weight: bold;
  margin-left: 10px;
  font-size: 30px;
  width: 30%;
  margin-left: 150px;
}

.email {
  background-color: green;
  /* font-weight: bold; */
  padding: 10px;
  /* width: 15%; */
  color: white;
  font-size: 20px;
  /* width: 200px; */
  /* margin-left: 10px; */
  /* height: 100%; */

  /* position: relative; */
  /* margin: auto; */
  margin-left: 150px;
}
</style>
