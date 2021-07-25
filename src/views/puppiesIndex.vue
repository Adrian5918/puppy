<template>
  <div class="puppiesIndex">
    <h1>{{ message }}</h1>
    <div v-for="puppy in puppies">
    <p> Name: {{ puppy.name}} </p>
    <p> Age: {{ puppy.age}} </p>
    <p> Breed: {{ puppy.breed}} </p>
    <hr>
    </div>
  </div>
</template>

<style></style>

<script>
import axios from "axios";
  export default {
    data: function () {
      return {
        message: "This is the puppy index!",
        puppies: [],
      };
    },
    created: function () {
      this.puppiesIndex();
    },
    methods: {
      puppiesIndex: function() {
        console.log('showing dogs...');
        axios.get('http://localhost:3000/puppies').then(response => {
          response.data
          console.log(response.data);
          this.puppies = response.data;
        })
      }
    },
  };
</script>
