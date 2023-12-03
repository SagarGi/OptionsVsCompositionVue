
<template>
  <p>Hello</p>
  <h1>{{ msg }}</h1>
  <p>{{name}}</p>
</template>
<script>
import {ref, reactive, toRefs} from "vue";
export default {
  props: {
    msg: String
  },
  setup(props) {
    const { msg } = props
    const name = ref('Sagar Gurung')
    return {
      name,
      msg
    }
  }
}
</script>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
