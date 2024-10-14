CourseCard.vue 

<template>
    <div class="course-card">
      <img :src="course.image" :alt="course.title + ' Icon'">
      <h2>{{ course.title }}</h2>
      <p>Price: ${{ course.price }}</p>
      <p>Duration: {{ course.duration }}</p>
      <p>Location: {{ course.location }}</p>
      <p>Available spaces: <span class="spaces">{{ course.availableSpaces }}</span></p>
      <button @click="addToCart" :disabled="course.availableSpaces <= 0">Add to Cart</button>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      course: Object,
      onAddToCart: Function
    },
    methods: {
      addToCart() {
        this.onAddToCart(this.course);
      }
    }
  }
  </script>
  
  <style scoped>
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
  