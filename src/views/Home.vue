<template>
  <div class="home">
    <h1>See all the People</h1>

    <div>
      <h4>People Count: {{ people.length}}</h4>
    </div>

    <div>
      New Person: <input v-model="newPerson.name">
      New Bio: <input v-model="newPerson.bio">
      <button v-on:click="addPerson()">Add Person!</button>
    </div>

    <div v-for="person in people">
      <h2 @click="toggleBio(person)">Name: {{ person.name }}</h2>
      <div v-if="person.bioVisible">
        <h3>Bio: {{ person.bio }}</h3>
        <button @click="deletePerson(person)">Delete Person!</button>
      </div>
    </div>

  </div>
</template>

<style>
  .strike {
    text-decoration: line-through;
  }
</style>

<script>
var axios = require('axios');

export default {
  data: function() {
    return {
      people: [],
      newPerson: {name: "", bio: "", bioVisible: true}
    };
  },
  created: function() {
    axios
    .get("http://localhost:3000/api/people")
    .then(function(response) {
      this.people = response.data;
    }.bind(this));
  },
  methods: {
    addPerson: function() {
      if (this.newPerson.name && this.newPerson.bio) {
      this.people.push(this.newPerson);
      this.newPerson = {name: "", bio: "", bioVisible: true};
      }
    },
    deletePerson: function(inputPerson) {
      var index = this.people.indexOf(inputPerson);
      this.people.splice(index, 1);
    },
    toggleBio: function(inputPerson) { 
        inputPerson.bioVisible = !inputPerson.bioVisible;
      }
  },
  computed: {}
};
</script>