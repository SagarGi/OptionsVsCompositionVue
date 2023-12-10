<template>
  <h1>Option API Demo</h1>
  <p>Name: {{ name }}</p>
  <p>Age: {{ age }}</p>
  <p>Voting Status : {{ getVotingStatus }}</p>
  <p>Born Year : {{ bornYear }}</p>
  <button @click="increaseAge">Age++</button>
  <button @click="decreaseAge">Age--</button>
</template>
<script>
export default {
  data() {
    return {
      name: "Sagar Gurung",
      age: 26,
      bornYear: 1997,
      votingStatus: "Eligible!",
    };
  },
  methods: {
    increaseAge() {
      this.age++;
    },
    decreaseAge() {
      this.age--;
    },
  },
  computed: {
    getVotingStatus() {
      return this.age >= 18 ? "Eligible" : "Not Eligible";
    },
  },
  watch: {
    age(oldAge, newAge) {
      if (oldAge > newAge) {
        this.bornYear--;
      } else {
        this.bornYear++;
      }
    },
  },
};
</script>

<style scoped></style>
