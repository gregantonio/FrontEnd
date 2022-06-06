<template>
  <div class="hello">
    <Header />
    <div class="container mrgnbtm">
          <div class="row">
            <div class="col-md-4">
                <DisplayBoard :numberOfUsers="numberOfUsers" @getAllUsers="getAllUsers()" />
            </div>
            <div class="col-md-4">
                <DisplayBoard2 :numberOfUsers="numberOfUsers" @getAllUsers="getAllUsers()" />
            </div>
            <div class="col-md-4">
                <DisplayBoard3 :numberOfUsers="numberOfUsers" @getAllUsers="getAllUsers()" />
            </div>
            <div class="col-md-12">
                <Spacer :numberOfUsers="numberOfUsers" @getAllUsers="getAllUsers()" />
            </div>
            <div class="col-md-8">
                <CreateUser @createUser="userCreate($event)" />
            </div>
            <div class="col-md-4">
                <DisplayCard :numberOfUsers="numberOfUsers" @getAllUsers="getAllUsers()" />
            </div>
          </div>
    </div>
    <div class="row mrgnbtm">
        <Users v-if="users.length > 0" :users="users" />
    </div>
  </div>
</template>

<script>
import Header from './Header.vue'
import CreateUser from './CreateUser.vue'
import DisplayBoard from './DisplayBoard.vue'
import DisplayBoard2 from './DisplayBoard2.vue'
import DisplayBoard3 from './DisplayBoard3.vue'
import DisplayCard from './DisplayCard.vue'
import Users from './Users.vue'
import Spacer from "./Spacer.vue"
import { getAllUsers, createUser } from '../services/UserService'

export default {
  name: 'Dashboard',
  components: {
    Header,
    CreateUser,
    DisplayBoard,
    DisplayBoard2,
    DisplayBoard3,
    DisplayCard,
    Spacer,
    Users
  },
  data() {
      return {
          users: [],
          numberOfUsers: 0
      }
  },
  methods: {
    getAllUsers() {
      getAllUsers().then(response => {
        console.log(response)
        this.users = response
        this.numberOfUsers = this.users.length
      })
    },
    userCreate(data) {
      console.log('data:::', data)
      createUser(data).then(response => {
        console.log(response);
        this.getAllUsers();
      });
    }
  },
  mounted () {
    this.getAllUsers();
  }
}
</script>