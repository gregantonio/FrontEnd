<template>
  <div class="wrapper">
    <!-- <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css"> -->
    <!-- <div class="row"> -->
       <!-- <h4>Search Flights</h4> -->
       <h5>{{title}}</h5>
        <form>
          <!-- <input type="text" v-model="inputText" placeholder = {{title}} /> -->
          
          <input type="text" v-model="inputText" placeholder = "Search" />
          <div v-if='open' class='matches'>
              <div v-for='match in matches' :key="match">{{match}}   </div>
          </div>
                <!-- v-model="email" name="email" id="email" aria-describedby="emailHelp" -->
                <!-- placeholder="Enter Information" -->
                <!-- {{ title }} -->
        <!-- <button type="button" @click='createUser()' class="btn btn-danger">Search</button> -->
        </form>
    <!-- </div> -->
  </div>
</template>

<script>
export default {
  name: 'CreateUser',
  data() {
    return {
      // title: 'hi',
      search:''
    }
  },
  props: {
    title: {
      type: String,
      required: true
    },
  },
  methods: {
      createUser() {
          console.log(this.firstName)
          const payload = {
              firstName: this.firstName,
              lastName: this.lastName,
              email: this.email
          }
          this.$emit('createUser', payload)
          this.clearForm();
      },
      clearForm() {
          this.firstName = "";
          this.lastName = "";
          this.email = "";
      }
  }
  // computed: {
  //   filteredItems:function(){
  //     return this.
  //   }
  // }
}
</script>