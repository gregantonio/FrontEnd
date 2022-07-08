<template>
  <div class="panel" @click="getMostPopularAirline()">
    <img :src="myImagePath" alt="something went wrong" style="width: 20%" />
    <!-- <p>{{ value }}</p>
    <i @click="$emit('icon-clicked', $event.target.value)">?</i> -->
    <!-- <h1 @click="myFunction()">CLICK ME! = {{ randomNumber }}</h1> -->
    <!-- <button @click="myFunction()">ClickMe</button> -->
   <h3 v-if="value==1">{{mostPopularAirline}}</h3>
     <h3 v-if="value==2">{{mostPopularDep}}</h3>
       <h3 v-if="value==3">{{mostPopularArrival}}</h3>
    <h4>{{ title }}</h4>
    
  </div>
</template>

<script>
import axios from 'axios';
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
    },
    methods: { 
      type: Function },
  },
  data() {
    return {
      mostPopularAirline: "Click me to find out!",
      mostPopularDep: "Click me to find out!",
      mostPopularArrival: "Click me to find out!",
    }
  },
  methods: {
    // myFunction() {
    //   this.randomNumber = Math.floor(Math.random()*100) //multiplied to get random number 0 - 100
    // }    
  },
  mounted() {
    axios({
        url: 'http://localhost:8080/ESProxy/flightdata/_search',
        method: 'POST',
        timeout: 0,
        headers: {
          'Content-Type': 'application/json'
        },
        data: JSON.stringify({
          "size": 0,
          "aggs": {
            "genres": {
              "terms": { "field": "airline.name.keyword" }
            }
          }
        })
      }).then((res) => {
      this.mostPopularAirline=res.data.aggregations.genres.buckets[0].key;
      });
    
  axios({
      url: 'http://localhost:8080/ESProxy/flightdata/_search',
      method: 'POST',
      timeout: 0,
      headers: {
        'Content-Type': 'application/json'
      },
      data: JSON.stringify({
      "size": 0, 
    "aggs": {
      "genres": {
        "terms": { "field": "departure.airport.keyword" }
      }
    }
  })
    }).then((res) => {
    this.mostPopularDep=res.data.aggregations.genres.buckets[0].key;
  });

  axios({
      url: 'http://localhost:8080/ESProxy/flightdata/_search',
      method: 'POST',
      timeout: 0,
      headers: {
        'Content-Type': 'application/json'
      },
      data: JSON.stringify({
      "size": 0, 
    "aggs": {
      "genres": {
        "terms": { "field": "arrival.airport.keyword" }
      }
    }
  })
    }).then((res) => {
    this.mostPopularArrival=res.data.aggregations.genres.buckets[0].key;
  });
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
  /* background-color: #ba6ddd;
  box-shadow: 0 2px rgb(0, 0, 0);
  transform: translateY(3px); */

}

/* Add some padding inside the card container */
.container {
  padding: 2px 16px;
}
</style>