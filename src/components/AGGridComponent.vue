<template>
    <div>
      <!-- The AG Grid component -->
      <ag-grid-vue
        :rowData="rowData"
        :columnDefs="colDefs"
        style="width: 100%; height: 500px;"
        class="ag-theme-quartz"
      >
      </ag-grid-vue>
    </div>
  </template>
  
  <script lang="ts">
  import { ref } from 'vue';
  import { AgGridVue } from 'ag-grid-vue3';
  import { ModuleRegistry } from '@ag-grid-community/core';
  import { ClientSideRowModelModule } from '@ag-grid-community/client-side-row-model';
  
  // Register AG Grid modules
  ModuleRegistry.registerModules([ClientSideRowModelModule]);
  
  export default {
    name: 'AGGridComponent',
    components: {
      AgGridVue,
    },
    setup() {
      // Row Data: The data to be displayed.
      const rowData = ref([
        { make: 'Tesla', model: 'Model Y', price: 64950, electric: true },
        { make: 'Toyota', model: 'Corolla', price: 29600, electric: false },
        { make: 'Ford', model: 'F-Series', price: 33850, electric: false },
        { make: 'Mercedes', model: 'EQA', price: 48890, electric: true },
        { make: 'Fiat', model: '500', price: 15774, electric: false },
        { make: 'Nissan', model: 'Juke', price: 20675, electric: false },
      ]);
  
      // Column Definitions: Defines the columns to be displayed.
      const colDefs = ref([
        { field: 'make' },
        { field: 'model' },
        { field: 'price' },
        { field: 'electric' }
      ]);
  
      return {
        rowData,
        colDefs,
      };
    },
  };
  </script>
  
  <style scoped>
  /* Add any custom styles if necessary */
  </style>
  