App.vue
<template> <!--Main container of the app-->
  <div>
    <h1>Available Courses</h1>
    <button @click="toggleCart">{{ showCart ? 'Go to Lessons' : 'Go to Cart' }}</button>

    <CourseList v-if="!showCart" @add-to-cart="updateCart" />   <!--if the cart isn't being displayed, the courselist component is displayed-->
    <Cart v-if="showCart" :cart="cart" /> <!--the cart components are shown when they schowCart is true, and the cart array is passed as a prop to the cart component-->
  </div>
</template>

<script>
import CourseList from './components/CourseList.vue';  
import Cart from './components/CartCopy.vue';
//imports the CourseList and Cart components


export default {  //register CourseList and Cart components
  components: {
    CourseList,
    Cart
  },
  data() {
    return {  
      showCart: false,  //a boolean to control whether to show the cart or the course list
      cart: []          //array to store the courses that are added into the cart
    };
  },
  methods: {
    toggleCart() {  //method to toggle between showing the cart or the courselist
      this.showCart = !this.showCart;
    },
    updateCart(course) {  //method to push new courses into the cart
      this.cart.push(course);
    }
  }
}
</script>

<style>
/*style for the toggle button*/
button {
  margin-top: 20px;
}
</style>
