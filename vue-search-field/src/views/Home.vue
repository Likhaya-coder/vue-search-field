<template>
  <div class="home">
    <h1>Home Page</h1>
    <input type="text" v-model="search" placeholder="Search">
    <p>You searched for {{search}}</p>
    <div class="names" v-for="name in matchingNames" :key="name">
      {{name}}
    </div>
  </div>
</template>

<script>
import { computed, ref } from '@vue/reactivity'
// @ is an alias to /src

export default {
  name: 'Home',
  setup() {
    const search = ref('')

    const names = ref(['Likhaya', 'Lwando', 'Lonwabo', 'Sikhumbuzo', 'Bongani', 'Luzuko', 'Mandilakhe'])

    const matchingNames = computed(() => {
      return names.value.filter((item) => item.includes(search.value))
    })

    return {search, names, matchingNames}
  }
}
</script>
<style scoped>
  .names {
    display: inline-block;
    background-color: #999;
    color: #000;
    padding: 20px;
    position: relative;
    margin: 10px 10px;
    border-radius: 10px;
    box-shadow: 1px 1px 7px black;
  }
  input {
    width: 300px;
    height: 45px;
    padding: 0 20px;
    font-size: 20px;
    border-radius: 50px;
  }
</style>