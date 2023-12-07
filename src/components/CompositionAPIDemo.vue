
<template>
  <h1>{{ msg }}</h1>
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
  props: {
    msg: String
  },
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
      if(data.age >= 18) {
        data.votingStatus = 'Eligible'
      } else {
        data.votingStatus = 'Not Eligible'
      }
      return data.votingStatus
    })

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
.read-the-docs {
  color: #888;
}
</style>



//reactive ref example :

// userInformation.value ={
//   name: 'lambu Gurung',
//   age: 17
// }
// userInformation.value.name = "lambu gurung"
// userInformation.value.age++
// }, 3000)
