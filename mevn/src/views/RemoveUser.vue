<template>
    <div><br><br>
        <div v-for="(user,index) in users" :key="user.id">
            <GetUsers/>
             <div class="forUser">
               
        <div class="sticky-sm-top">
            <p>{{ user.name }}</p>
            <p>{{ user.age }}</p> </div>
             </div>
            <button type="button" class="btn btn-outline-danger"  style="text-align:center" @click="deleteUser(index)">Remove</button>
            <br><br><br><br>
        </div>
  </div>
</template>

<script>
import { mapState } from "vuex";
import GetUsers from '@/components/GetUsers.vue'
export default {
  name: "RemoveUser",
  components: {
    GetUsers,
  },
    computed:mapState({
    users: state => state.users
  }),
  mounted() {
    this.$store.dispatch('getPosts'); 
  },
  methods: {
      async deleteUser(index) {
        this.$store.dispatch('deleteUser',index);
      }
  }
};
</script>
<style scoped>
.forUser {
  font-size: 25px;
  padding: 25px;
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