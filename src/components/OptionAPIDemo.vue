
<template>
  <h1>{{ msg }}</h1>
  <p>Name: {{name}}</p>
  <p>Age: {{age}}</p>
  <p>Voting Status : {{votingStatus}}</p>
  <p>Born Year : {{bornYear}}</p>
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
        age: 26,
        bornYear: 1997,
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
      age(oldAge, newAge) {
        if(oldAge > newAge) {
          this.bornYear--
        } else {
          this.bornYear++
        }
      }
    }
  }
</script>

<style scoped>

</style>
