<template>
  <div class="container grid-lg">
    <input v-model="quotes.test">
    <h1>{{quotes}}</h1>
  </div>
</template>

<script>
import { reactive, toRefs } from "vue";
import api from '@/services/api.js'

export default {
  name: "App",
  setup() {
    const data = reactive({
      quotes: {},
    });

    api.all().then(response => {
      data.quotes = response.data
    })
 
    return {...toRefs(data)}
  },
};
</script>
