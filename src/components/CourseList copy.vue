CourseList.vue
<template> <!--grid that displays list of all the courses-->
  <div class="course-grid">
    <CourseCard 
      v-for="course in courses"   
      :key="course.id" 
      :course="course" 
      :onAddToCart="handleAddToCart"
    />
    <!--V-for loops through each course in the courses array.The :course prop passes each course object to the CourseCard component -->
    <!-- The :onAddToCart prop passes the handleAddToCart method as a callback to be triggered in the child component -->
  </div>
</template>

<script>
import CourseCard from './CourseCard.vue'; //imports the CourseCard component so it can display individual course details

export default {
  components: {
    CourseCard  //registering CourseCard as a child component
  },
  data() {
    return {
      courses: [  //List of courses to be displayed 
        { id: 1, title: 'Math', price: 100, duration: '3 months', location: 'Room 101', availableSpaces: 5, image: 'math.png' },
        { id: 2, title: 'Biology', price: 100, duration: '4 months', location: 'Lab 202', availableSpaces: 5, image: 'bio.png' },
        { id: 3, title: 'Chemistry', price: 200, duration: '4 months', location: 'Lab 203', availableSpaces: 5, image: 'chem.png' },
        { id: 4, title: 'History', price: 100, duration: '3 months', location: 'Room 104', availableSpaces: 5, image: 'history.png' },
        { id: 5, title: 'French', price: 150, duration: '4 months', location: 'Room 105', availableSpaces: 5, image: 'french.png' },
        { id: 6, title: 'Spanish', price: 150, duration: '4 months', location: 'Room 106', availableSpaces: 5, image: 'spanish.png' },
        { id: 7, title: 'German', price: 150, duration: '4 months', location: 'Room 107', availableSpaces: 5, image: 'german.png' },
        { id: 8, title: 'Economics', price: 130, duration: '4 months', location: 'Room 108', availableSpaces: 5, image: 'econ.png' },
        { id: 9, title: 'Advanced Math', price: 500, duration: '5 months', location: 'Room 109', availableSpaces: 5, image: 'advanced_math.png' },
        { id: 10, title: 'Basic Algebra', price: 100, duration: '3 months', location: 'Room 110', availableSpaces: 5, image: 'algebra.png' }
      ],
      cart: []  //initializing an empty cart array to hold the courses added to the cart
    };
  },
  methods: {
    handleAddToCart(course) { //method to handle adding a course to the cart
      this.cart.push(course); //push the selected course object into the cart array
      course.availableSpaces -= 1; // Decrement available spaces
    }
  }
}
</script>

<style scoped> /*Styling for the course grid*/
.course-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}
</style>
