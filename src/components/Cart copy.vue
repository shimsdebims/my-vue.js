Cart.vue
<template>
  <div class="cart-section">
  <!-- Display the shopping cart heading -->
    <h1>Your Shopping Cart</h1>

      <!-- Iterate through the cart items passed via props, and display each one in a list -->  
    <ul>
      <li v-for="(item, index) in cart" :key="index">{{ item.title }}</li> <!--V-for loops through the cart array, and each item is displayed as a list. 'key' provides a unique identifier for each item-->
    </ul>

    <!--Checkout section-->
    <h2>Checkout</h2>
    <form @submit.prevent="submitOrder">  <!-- Form for collecting user's name and phone number -->
      <!-- @submit.prevent stops the default form submission behavior and triggers 'submitOrder' method -->
      <label for="name">Name:</label>
      <input type="text" v-model="name" required>
      <br>
      <label for="phone">Phone:</label>
      <input type="text" v-model="phone" required>
      <br>
      <button :disabled="!isValid" type="submit">Checkout</button>
    </form>
  </div>  <!--this section provides prompts for users to fill for the checkout, and checks through 'isValid' before letting the user checkout-->
</template>

<script>
export default {
  props: {
    cart: Array   //cart is passed as a prop from the parent component and is identified as an array
  },
  data() {
    return {
      name: '',
      phone: ''
    };  //name and phone number are returned 
  },
  computed: {
    isValid() {   //Checks if both name and phone number inputs are valid
      const nameValid = /^[a-zA-Z\s]+$/.test(this.name); //checks to make sure its only letters and spaces
      const phoneValid = /^\d+$/.test(this.phone);   //checks to make sure its only numerical digits
      return nameValid && phoneValid;     //returns true if both are valid
    }   
  },
  methods: {    //method triggered when checkout form is submitted 
    submitOrder() {
      alert('Order submitted!');
       // For now, it just displays an alert indicating the order was submitted..I'll change to put actual logic that handles the order submissions
    }
  } 
}
</script>

<style scoped>
/*CSS styles*/
.cart-section {
  display: block;
}
</style>
