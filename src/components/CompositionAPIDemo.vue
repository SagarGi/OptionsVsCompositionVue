
<template>
  <h1>CompositionAPI Demo</h1>
  <p>Name: {{name}}</p>
  <p>Age: {{age}}</p>
  <p>Voting Status : {{getVotingStatus}}</p>
  <p>Born Year : {{bornYear}}</p>
  <button @click="increaseAge">Age++</button>
  <button @click="decreaseAge">Age--</button>
</template>
<script>
import { reactive, toRefs, computed , watch} from "vue";
export default {
  setup() {
    // data
    const data = reactive({
      name: 'Sagar Gurung',
      age: 26,
      votingStatus: "Not Eligible",
      bornYear: 1997
    })

    const mainData = toRefs(data)

    // methods
    function increaseAge() {
      data.age++
    }

    function decreaseAge() {
      data.age--
    }

    //computed
    const getVotingStatus = computed(() => {
      return (data.age >= 18) ? 'Eligible' : 'Not Eligible'
    })

    //watcher
    watch(mainData.age, (oldAge, newAge) => {
      if(oldAge > newAge) {
        data.bornYear--
      } else {
        data.bornYear++
      }
    })


    return {
      ...mainData,
      increaseAge,
      decreaseAge,
      getVotingStatus
    }
  }
}
</script>

<style scoped>
</style>
