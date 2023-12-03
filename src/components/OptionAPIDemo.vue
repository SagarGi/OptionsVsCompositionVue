
<template>
  <p>Hello</p>
  <h1>{{ msg }}</h1>
  <p>{{this.name}}</p>
</template>
<script>
  export default {
    props: {
      msg: String
    },
    data() {
      return {
        name: 'Sagar Gurung',
      }
    },
    methods() {

    },
    computed: {

    },
    watch() {

    }
  }
</script>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
