<template>
  <ag-grid-vue
    style="width: 930px; height: 335px"
    class="ag-theme-alpine"
    :columnDefs="columnDefs"
    :rowData="rowData"
    :filterKey="searchQuery"
    enableSorting:true
>
  </ag-grid-vue>
</template>

<style>
.ag-header-cell-label{
    justify-content: center;
}

</style>

<script>
import "ag-grid-community/dist/styles/ag-grid.css";
import "ag-grid-community/dist/styles/ag-theme-alpine.css";
import { AgGridVue } from "ag-grid-vue3";

export default {
  name: "App",
  components: {
    AgGridVue,
  },
  setup() {
    return {
      columnDefs: [
        { headerName: "Flight", field: "flight", filter: true, width: 185},
        { headerName: "Departure", field: "departure", filter: true, width: 185},
        { headerName: "Destination", field: "destination", filter: true, width: 185},
        { headerName: "Date", field: "date", filter: true, width: 185},
        { headerName: "Rating", field: "rating", filter: true, width: 185},        
      ],
      rowData: [
        { flight: "Flight 1", departure: "Celica", destination: "Rome", date: "6/17/22", rating: "1"},
        { flight: "Flight 2", departure: "Mondeo", destination: "Virginia", date: "6/17/22", rating: "2"},
        { flight: "Flight 3", departure: "Boxster", destination: "Key West", date: "6/17/22", rating: "3"},
        { flight: "Flight 4", departure: "Celica", destination: "Rome", date: "6/17/22", rating: "4"},
        { flight: "Flight 5", departure: "Mondeo", destination: "Virginia", date: "6/17/22", rating: "5"},
        
      ],
    };
  },
};


</script>
