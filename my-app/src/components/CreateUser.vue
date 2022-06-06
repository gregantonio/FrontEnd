<template>
  <div class="container">
    <div class="row">
        <div class="col-md-12 mrgnbtm">
       <h4>Search Flights</h4>
            <form>
                <div class="row">
                    <div class="form-group col-md-12">
                        <input type="text" class="form-control" v-model="email" name="email" id="email" aria-describedby="emailHelp" placeholder="Enter Information" />
                    </div>
                </div>
                <button type="button" @click='createUser()' class="btn btn-danger">Search</button>
            </form>
        </div>
    </div>
    </div>
</template>

<script>
export default {
  name: 'CreateUser',
  data() {
    return {
      firstName: '',
      lastName: '',
      email: ''
    }
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
}
</script>