<template>
  <div class="home">
    <h1>{{ message }}</h1>

    <div>
      New Person: <input v-model="newPerson.text">
      <button v-on:click="addPerson()">Add Person!</button>
    </div>

    <div v-for="person in people">
      <h3>{{ person.name}}</h3>
    </div>
  </div>
</template>

<style>
</style>

<script>
export default {
  data: function() {
    return {
      message: "See all the People",

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
      name: "Shiva",
      bio: "Hindi",
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
    }
  },
  computed: {}
};
</script>