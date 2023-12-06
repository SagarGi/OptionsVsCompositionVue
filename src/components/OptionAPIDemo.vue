
<template>
  <h1>{{ msg }}</h1>
  <p>Name: {{this.name}}</p>
  <p>Age: {{this.age}}</p>
  <p>Voting Status : {{this.votingStatus}}</p>
  <button @click="increaseAge">Age++</button>
  <button @click="decreaseAge">Age--</button>
</template>
<script>
  export default {
    props: {
      msg: String
    },
    data() {
      return {
        name: 'Sagar Gurung',
        age: 17,
        year: 1997,
        votingStatus: 'Not Eligible!'
      }
    },
    methods: {
      increaseAge() {
        this.age++
      },
      decreaseAge() {
        this.age--
      }
    },
    computed: {
      getVotingStatus() {
        if(this.age >= 18) {
          this.votingStatus = 'Eligible'
        } else {
          this.votingStatus = 'Not Eligible'
        }
        return this.votingStatus
      }
    },
    watch: {
      age(newAge, oldAge) {
        if(newAge >= 18) {
          this.votingStatus = 'Eligible'
        } else {
          this.votingStatus = 'Not Eligible'
        }
      }
    }
  }
</script>

<style scoped>

</style>
