CourseList.vue
<template>
  <div class="course-grid">
    <CourseCard 
      v-for="course in courses" 
      :key="course.id" 
      :course="course" 
      :onAddToCart="handleAddToCart"
    />
  </div>
</template>

<script>
import CourseCard from './CourseCard.vue';

export default {
  components: {
    CourseCard
  },
  data() {
    return {
      courses: [
        { id: 1, title: 'Math', price: 100, duration: '3 months', location: 'Room 101', availableSpaces: 5, image: 'math.png' },
        { id: 2, title: 'Biology', price: 120, duration: '4 months', location: 'Lab 202', availableSpaces: 5, image: 'bio.png' },
        { id: 3, title: 'Chemistry', price: 110, duration: '4 months', location: 'Lab 203', availableSpaces: 5, image: 'chem.png' },
        { id: 4, title: 'History', price: 90, duration: '3 months', location: 'Room 104', availableSpaces: 5, image: 'history.png' },
        { id: 5, title: 'French', price: 100, duration: '4 months', location: 'Room 105', availableSpaces: 5, image: 'french.png' },
        { id: 6, title: 'Spanish', price: 100, duration: '4 months', location: 'Room 106', availableSpaces: 5, image: 'spanish.png' },
        { id: 7, title: 'German', price: 110, duration: '4 months', location: 'Room 107', availableSpaces: 5, image: 'german.png' },
        { id: 8, title: 'Economics', price: 130, duration: '4 months', location: 'Room 108', availableSpaces: 5, image: 'econ.png' },
        { id: 9, title: 'Advanced Math', price: 140, duration: '5 months', location: 'Room 109', availableSpaces: 5, image: 'advanced_math.png' },
        { id: 10, title: 'Basic Algebra', price: 90, duration: '3 months', location: 'Room 110', availableSpaces: 5, image: 'algebra.png' }
      ],
      cart: []
    };
  },
  methods: {
    handleAddToCart(course) {
      this.cart.push(course);
      course.availableSpaces -= 1; // Decrement available spaces
    }
  }
}
</script>

<style scoped>
.course-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}
</style>
