<template>
    <div><br><br>
        <div v-for="(user,index) in users" :key="user.id">
            <GetUsers/>
            <div class="forUser">
              <div class="sticky-sm-top">
                <p>{{ user.name }}</p>
                <p>{{ user.age }}</p>  
                 </div>
            </div>
            <input type="text" class="form-control" placeholder="Name" aria-label="Name" aria-describedby="addon-wrapping" style="
           display: inline-block;" v-model="user.name"><br>
            <br><input type="text" class="form-control" placeholder="Age" aria-label="Age" aria-describedby="addon-wrapping" style="display: inline-block;"  v-model="user.age">
            <br><br>
            <button type="button" class="btn btn-primary"  style="text-align:center" @click="changeUser(index)">Change</button>
            <br><br><br><br>
        </div>
  </div>
</template>

<script>
import 'bootstrap'; 
import 'bootstrap/dist/css/bootstrap.min.css';

import { mapState } from "vuex";
import GetUsers from '@/components/GetUsers.vue'

export default {
  name: "ChangeUser",
  components: {
    GetUsers,
  },
    computed : mapState({
    users: state => state.users
  }),
  mounted() {
    this.$store.dispatch('getPosts');
  },
  methods: {
      async changeUser(index) {
        this.$store.dispatch('changeUser',index); 
      }
  }
};
</script>

<style scoped>
.forUser {
  font-size: 25px;
  padding: 25px 100px;
  margin: 0px 700px;
  border: 3px #000000 solid;
  border-radius: 15px;
  height: 150px;
  width: auto;
  margin-bottom: 25px;
}
.deleteUser {
  border: 1px solid red;
  width: 300px;
  height: 200px;
  position: fixed;
  background: violet;
}
input::placeholder {
  padding: 3px;
  background: orange;
}
input {
  width: 240px;
  align-items: center;
}
</style>