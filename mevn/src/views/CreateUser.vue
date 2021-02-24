<template>
  <div>
    <div class="input-group flex-nowrap">
    <input type="text" class="form-control" placeholder="Name" aria-label="Name" aria-describedby="addon-wrapping" style="margin:50px 50px 50px 700px;" v-model="addUser.name">
    <input type="text" class="form-control" placeholder="Age" aria-label="Age" aria-describedby="addon-wrapping" style="margin:50px 700px 50px 50px;" v-model="addUser.age">
    </div>
	<button type="button" class="btn btn-outline-success" style="text-align:center" @click="createUser()">Create</button>
  </div>
</template>

<script>
import 'bootstrap'; 
import 'bootstrap/dist/css/bootstrap.min.css';

export default {
  name: "CreateUser",
  data: () => {
      return {addUser: {name: null,age: null}}
  },
  methods: {
      async createUser() {
        this.$store.dispatch('addUser',this.addUser);
        this.addUser="";
      }
  }
};
</script>
<style scoped>
</style>