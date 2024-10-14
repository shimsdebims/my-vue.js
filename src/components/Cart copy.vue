Cart.vue
<template>
  <div class="cart-section">
    <h1>Your Shopping Cart</h1>
    <ul>
      <li v-for="(item, index) in cart" :key="index">{{ item.title }}</li>
    </ul>

    <h2>Checkout</h2>
    <form @submit.prevent="submitOrder">
      <label for="name">Name:</label>
      <input type="text" v-model="name" required>
      <br>
      <label for="phone">Phone:</label>
      <input type="text" v-model="phone" required>
      <br>
      <button :disabled="!isValid" type="submit">Checkout</button>
    </form>
  </div>
</template>

<script>
export default {
  props: {
    cart: Array
  },
  data() {
    return {
      name: '',
      phone: ''
    };
  },
  computed: {
    isValid() {
      const nameValid = /^[a-zA-Z\s]+$/.test(this.name);
      const phoneValid = /^\d+$/.test(this.phone);
      return nameValid && phoneValid;
    }
  },
  methods: {
    submitOrder() {
      alert('Order submitted!');
      // Here you can handle the order submission logic
    }
  }
}
</script>

<style scoped>
.cart-section {
  display: block;
}
</style>
