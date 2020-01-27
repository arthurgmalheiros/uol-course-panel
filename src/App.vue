<template>
  <v-app>
    <v-content>
      <DataTable />
    </v-content>
  </v-app>
</template>

<script lang="ts">
import Vue from "vue";
import DataTable from "./components/DataTable.vue";

export default Vue.extend({
  name: "App",

  components: {
    DataTable
  },

  data: () => ({
    //
  })
});
</script>
