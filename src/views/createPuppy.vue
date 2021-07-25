<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <div> name:
      <input type="text" v-model="newPuppyParams.name" />
      <br>
      age:
      <input type="text" v-model="newPuppyParams.age" />
      <br>
      breed:
      <input type="text" v-model="newPuppyParams.breed" />
      <br>
      <button v-on:click="createPuppy()">Create new puppy</button>
      <br>
    </div>
  </div>
</template>

<style></style>

<script>
import axios from "axios";
  export default {
    data: function () {
      return {
        message: "Welcome to the dog create action",
        newPuppyParams: {},
      };
    },
    created: function () {
      this.puppies = Response.data;
    },
    methods: {
      createPuppy: function() {
        console.log('creating dog');
        axios.post('http://localhost3000/puppies', this.newPuppyParams)
        .then(response => { 
          console.log('creating', response);
          this.puppies.push(response.data);
          this.newPuppyParams = {};
        })
        .catch((error) => {
          console.log('puppy create error', error.response);
        });
      }
    },
  };
</script>
