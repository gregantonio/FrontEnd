<template>
  <div class="panel">
    <div class="panel-inner">
      <div class="panel-front">
    <!-- <h4><img src="https://cdn-icons-png.flaticon.com/512/447/447031.png" alt="Image" style="width: 25%" /></h4> -->
        <img :src="myImagePath" alt="something went wrong" style="width: 20%" />
      </div>
      <div class="panel-back">
        <p>{{ value }}</p>
        <h4>{{ title }}</h4>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Panel",
  props: {
    title: {
      type: String,
      required: true
    },
    myImagePath: {
      type: String,
      required: true
      // "title","src"
    },
    value: {
      type: Number,
      required: true
    }
  }
}
</script>

<style scoped>
.panel {
  /* Add shadows to create the "card" effect */
  box-shadow: 0 2px 8px 0 rgba(0, 0, 0, 0.2);
  padding: 20px 0px;
  width: 100%;
  border-radius: 4px;
  transition: all var(--input-quick);
  perspective: 1000px;
}

.panel-inner{
  position: relative;
  width: 100%;
  height: 100%;
  text-align: center;
  transition: 0.8s;
  transform-style: preserve-3d;  
}

/* On mouse-over, add a deeper shadow 
 * offset-x | offset-y | blur-radius | spread-radius | color */
.panel:hover {
  box-shadow: 0 8px 16px 17px rgba(0, 0, 0, 0.2);
  background-color: var(--input-color-light);
  /* transform: rotateY(180deg);  */
}

/* On mouse-click,  */
/* .panel:click {
  box-shadow: 0 8px 16px 12px rgba(0, 0, 0, 0.2);
} */

.panel:active{
  /* transform: rotateY(180deg);  */
  background-color: #ba6ddd;
  box-shadow: 0 2px rgb(0, 0, 0);
  transform: translateY(3px);
}

/* Add some padding inside the card container */
.container {
  padding: 2px 16px;
}
</style>