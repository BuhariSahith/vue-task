<template>
  <v-data-table :headers="headers" :items="mockData" :sort-by="['weight']" :items-per-page=mockData.length hide-default-footer
    :sort-desc="[false, true]" class="elevation-1"></v-data-table>
</template>
<script>
import { mockData } from "@/mock-data/mockdata";
export default {

  data() {
    return {
      headers: [
        {
          text: 'Name',
          align: 'start',
          sortable: false,
          value: 'name',
        },
        { text: 'Age', value: 'age', sortable: false, },
        { text: 'Weight', value: 'weight' },
        { text: 'Height', value: 'height', sortable: false, },
        { text: 'Class', value: 'class', sortable: false, },
      ],
      mockData
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
