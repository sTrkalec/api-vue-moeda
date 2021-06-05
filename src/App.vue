  
<template>
  <div class="container grid-lg my-2 py-2">
    <div class="card mb-2" v-if="listenQuotes.length > 0">
      <div class="card-header">
        <div class="h4">Acompanhando</div>
      </div>
      <div class="card-body">
      </div>
    </div>

    <div class="card">
      <div class="card-header">
        <div class="h4">Todas as moedas</div>
      </div>
      <div class="card-body">
        <ListQuotes
          :quotes="quotes"
          :listen-quotes="listenQuotes"


        />
      </div>
    </div>
  </div>
</template>

<script>
import { onMounted, reactive, toRefs } from "vue";
import api from "@/services/api";
import ListQuotes from "./components/ListQuotes";
export default {
  name: "App",
  components: { ListQuotes},
  setup() {
    const data = reactive({
      quotes: {},
      listenQuotes: [],
    });
    onMounted(async () => {
      const response = await api.all();
      data.quotes = response.data;
    });
  
    return {
      ...toRefs(data),
    };
  },
};
</script>