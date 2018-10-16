<template>
  <div class="home">
    <h1>See all the People</h1>

    <div>
      New Person: <input v-model="newPerson.name">
      New Bio: <input v-model="newPerson.bio">
      <button v-on:click="addPerson()">Add Person!</button>
    </div>

    <div v-for="person in people">
      <h3>Name: {{ person.name }}</h3>
      <p>Bio: {{ person.bio }}</p>
      <button v-on:click="deletePerson()">Delete Person!</button>

    </div>

    <div>
      <br>
      <h4>People Count: {{this.people.length}}</h4>
    </div>

  </div>
</template>

<style>
  body {
    background-color: #61D9F3;
  }
</style>

<script>
export default {
  data: function() {
    return {

      people: [
      { 
        name: "Buddha",
        bio: "Buddhist",
        bioVisible: true
      },
      { 
        name: "Jesus",
        bio: "Jewish",
        bioVisible: true
      },
      {
        name: "Steve",
        bio: "Agnostic",
        bioVisible: true
      }
    ],
    newPerson: {name: "", bio: "", bioVisible: true}
    };
  },
  created: function() {},
  methods: {
    addPerson: function() {
      this.people.push(this.newPerson);
      this.newPerson = {name: "", bio: "", bioVisible: true};
    },
    deletePerson: function() {
      this.people.splice(this.people.index, 1);
      return people;
    }
  },
  computed: {}
};
</script>