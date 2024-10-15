CourseCard.vue 

<template>  <!-- this is for the individual course components-->
    <div class="course-card">   <!--Displays the course, its image, duration, etc. info on the course-->
      <img :src="course.image" :alt="course.title + ' Icon'">
      <h2>{{ course.title }}</h2>
      <p>Price: ${{ course.price }}</p>
      <p>Duration: {{ course.duration }}</p>
      <p>Location: {{ course.location }}</p>
      <p>Available spaces: <span class="spaces">{{ course.availableSpaces }}</span></p>
      <button @click="addToCart" :disabled="course.availableSpaces <= 0">Add to Cart</button> <!--triggers 'addToCart' when clicked-->
    </div>
  </template>
  
  <script>
  export default {
    props: {  
      course: Object, //contains/takes the components/details from the course-cards (above)
      onAddToCart: Function   //function (passed from the parent) that handles the 'addToCart' logic
    },
    methods: {
        // Method to trigger the parent function 'onAddToCart' with the current course as an argument
      addToCart() {
        this.onAddToCart(this.course);
      }
    }
  }
  </script>
  
  <style scoped>  /*style for the indiv. course cards*/
  .course-card {
    border: 1px solid #ddd;
    padding: 20px;
    text-align: center;
  }
  .course-card img {
    width: 100px;
    height: 100px;
  }
  </style>
  