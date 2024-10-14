App.vue
<template>
  <div>
    <h1>Available Courses</h1>
    <button @click="toggleCart">{{ showCart ? 'Go to Lessons' : 'Go to Cart' }}</button>

    <CourseList v-if="!showCart" @add-to-cart="updateCart" />
    <Cart v-if="showCart" :cart="cart" />
  </div>
</template>

<script>
import CourseList from './CourseList.vue';
import Cart from './Cart.vue';

export default {
  components: {
    CourseList,
    Cart
  },
  data() {
    return {
      showCart: false,
      cart: []
    };
  },
  methods: {
    toggleCart() {
      this.showCart = !this.showCart;
    },
    updateCart(course) {
      this.cart.push(course);
    }
  }
}
</script>

<style>
button {
  margin-top: 20px;
}
</style>
