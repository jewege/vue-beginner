<template>
  <div>
    <h1>Vue for beginners</h1>
    <UserView />
    <router-view />
  </div>
</template>
<script>
import UserView from "./views/UserView.vue";
export default {
  components: {
    UserView,
  },
};
</script>
<style></style>
