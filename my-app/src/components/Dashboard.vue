<template>
  <div class="hello">
    <Header />
    <div class="container">
      <!-- <div class="col">
                <DisplayBoard :numberOfUsers="numberOfUsers" @getAllUsers="getAllUsers()" />
            </div> -->
      <!-- <ChildComponent @send-message="handleSendMessage" /> -->
      <Panel title="Most Popular Airline"  myImagePath="https://cdn-icons-png.flaticon.com/512/723/723955.png" value=1 />
      <Panel title="Most Popular Departure" myImagePath="https://cdn-icons-png.flaticon.com/512/68/68380.png" value=2 />
      <Panel title="Most Popular Destination" myImagePath="https://cdn-icons-png.flaticon.com/512/447/447031.png" value=3 />
      <!-- <div class="col">
                <Spacer :numberOfUsers="numberOfUsers" @getAllUsers="getAllUsers()" />
            </div>
            <div class="col">
                <CreateUser @createUser="userCreate($event)" />
            </div>
            <div class="col">
                <DisplayCard :numberOfUsers="numberOfUsers" @getAllUsers="getAllUsers()" />
            </div> -->
    </div>
    <div class="container2">
      <div class="buttoncontainer">
        <!-- insert buttons for grid here -->
        <!-- <CreateUser @createUser="userCreate($event)" text="hello"/>
        <CreateUser @createUser="userCreate($event)" text="hello"/>
        <CreateUser @createUser="userCreate($event)" text="hello"/>
        <CreateUser @createUser="userCreate($event)" text="hello"/>
        <CreateUser @createUser="userCreate($event)" text="hello"/> -->
        <CreateUser title="Flight"/>
        <CreateUser title="Departure"/>
        <CreateUser title="Destination"/>
        <CreateUser title="Date"/>

        <!-- <FTButton big>Flight</FTButton>
        <FTButton big>Departure</FTButton>
        <FTButton big>Destination</FTButton>
        <FTButton big>Date</FTButton>
        <FTButton big>Rating</FTButton>
        <TextSearch big>Rating</TextSearch> -->
      </div>
      <div class="gridcontainer">
        <!-- insert buttons for grid here -->
        <AGDataGrid class="grid" />
      </div>
    </div>
    <!-- <div class="row mrgnbtm">
        <Users v-if="users.length > 0" :users="users" />
    </div> -->
  </div>
</template>

<style scoped>
.container {  
  display: flex;
  flex-direction: row;
  align-items: center;
  gap: 10px;
  padding: 10px;
  /* margin-bottom: 10px; */
}
.container2{
  display:flex;
  flex-direction: row;
  /* gap: 10px; */
}
.buttoncontainer {
  display: flex;
  flex-direction: column;
  /* height: 100%; */
  width: 40%;
  /* width: 77.5rem; */
  justify-content: center;
  align-items: center;
  /* padding: 10px; */
  margin-left: 10px;
  margin-right: 10px;
  /* margin-bottom: 10px; */
  margin-top: -33px;
  /* gap: 20px; */

  /* justify-content: space-apart; */
}

.gridcontainer{
  display: flex;
  /* height: 100%; */
  /* width: 40%; */
  /* width: 77.5rem; */
  /* justify-content: center; */
  /* align-items: center; */
  /* padding: 10px; */
  /* margin-top: 10px; */
  margin-right: 10px;
  margin-bottom: 10px;
  /* gap: 10px; */
}

.container .col {
  background: lightblue;
}

.container .col p {
  padding: 0.25rem 0.75rem;
}

</style>

<script>
import Header from "./Header.vue";
import CreateUser from './CreateUser.vue';
// import DisplayBoard from './DisplayBoard.vue'
// import DisplayCard from './DisplayCard.vue'
// import Users from './Users.vue'
import Panel from "./Panel.vue";
// import FTButton from "./inputs/FTButton.vue";
// import TextSearch from "./inputs/TextSearch.vue";
import AGDataGrid from "./AGDataGrid.vue";

import { getAllUsers, createUser } from "../services/UserService";

// import { IMAGE_PATH } from "./constants.js";
// import {var1 as airline, var2 as departure, var3 as destination} from "./constants.js";

// export const IMAGE_PATH;
// export {var1, var2, var3};

export default {
  name: "Dashboard",
  components: {
    Header,
    CreateUser,
    // DisplayBoard,
    // Users,
    AGDataGrid,
    Panel,
    // FTButton,
    // TextSearch,
  },
  data() {
    return {
      users: [],
      numberOfUsers: 0,
    };
  },
  methods: {
    getAllUsers() {
      getAllUsers().then((response) => {
        console.log(response);
        this.users = response;
        this.numberOfUsers = this.users.length;
      });
    },
    userCreate(data) {
      console.log("data:::", data);
      createUser(data).then((response) => {
        console.log(response);
        this.getAllUsers();
      });
    },
    handleSendMessage(event, value2) {
      //Our event handler gets the event, as well as any arguments
      //the child passes to the event
      console.log('From the child:', value2);
    }
  },
  mounted() {
    // const res = axios.get() <-- insert local host proxy url to make request to backend server
    this.getAllUsers();
  },
};
</script>

