<template>
  <div>
    <br><br>
    <div v-for="user in users" :key="user.id" >
        <GetUsers/>
        <div class="forUser">
        <div class="sticky-sm-top">
          <p>{{ user.name }}    {{ user.age }}</p>
        </div>   </div>
      <br>
  </div>
  </div>
</template>

<script>
import 'bootstrap'; 
import 'bootstrap/dist/css/bootstrap.min.css';

import { mapState } from "vuex";
import GetUsers from '@/components/GetUsers.vue'
export default {
  name: "Users",
  components: {
    GetUsers,
  },
  computed:mapState({
    users: state => state.users
  }),
  mounted() {
    this.$store.dispatch('getPosts'); 
  }
};
</script>
<style scoped>
.forUser {
  font-size: 25px;
  padding: 30px;
  margin: 0px 700px;
  border: 3px #000000 solid;
  border-radius: 15px;
  height: 110px;
  width: auto;
  margin-bottom: 25px;
}
</style>