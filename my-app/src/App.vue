<template>
  <div id="app">
    <!-- <FTButton>Hello World</FTButton> -->
    <!-- <FTButton big>Hello World</FTButton> -->
    <!-- <FTButton priority="secondary">Hello World</FTButton> -->
    <Dashboard v-if="settings" /> 
    <!-- <ejs-combobox> -->
    <!-- </ejs-combobox> -->
    <!-- <AGDataGrid>Grid</AGDataGrid> -->
  </div>
</template>

<script>
//import 'bootstrap/dist/css/bootstrap.css'
//import 'bootstrap-vue/dist/bootstrap-vue.css'
// import { ComboBoxPlugin } from '@syncfusion/ej2-vue-dropdowns';
import Dashboard from "./components/Dashboard.vue";
// import FTButton from "./components/inputs/FTButton.vue";
// import AGDataGrid from './components/AGDataGrid.vue'

export default {
  name: "App",
  components: {
    Dashboard,
    // FTButton,
    // AGDataGrid,
    // ComboBoxPlugin,
  },
  data() {
    return {
      settings: false,
    };
  },
  mounted() {
    console.log("I am in mounted!!!");
    this.settings = true;
  },
  setup() {
    console.log("I am in setup!!!");
  },
};
</script>

<style>
html,
body {
  height: 100%;
  width: 100%;
  position: fixed;
  margin: 0px;
  box-sizing: border-box;
}
@import "./assets/styles/global.css";
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  /* font-family: 'Courier New'; */
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #ffffff;
  margin-top: 0px;
  background-color: rgb(91, 91, 91);
  height: 100%;
}

/*global css variables*/
:root {
  --input-quick: 0.1s;
  --input-color: #ba6ddd;
  --input-color-light: #ca7ded;
  --shade-light: rgb(255, 255, 255);
}
</style>