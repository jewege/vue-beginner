<template>
  <div>
    Users
    <UserList :users="users" @removeUser="removeUser" @addUser="addUser"></UserList>
  </div>
</template>

<script>
import axios from "axios";
import UserList from "@/components/UserList";

export default {
  name: "UsersView",
  components: { UserList },
  data() {
    return {
      users: [],
    };
  },
  methods: {
    removeUser(id) {
      axios.delete(`http://localhost:3000/users/${id}`).then(() => {
        this.users = this.users.filter((user) => user.id !== id);
      });
    },
    addUser(newUserName) {
      // const uniqueId = Math.random().toString(16);
      const newUser = {
        name: newUserName,
        age: 30,
      };
      axios.post("http://localhost:3000/users", newUser).then((response) => {
        console.log("response", response.data);
        this.users.push(response.data);
      });
    },
  },
  mounted() {
    axios.get("http://localhost:3000/users").then((response) => {
      this.users = response.data;
    });
  },
};
</script>
