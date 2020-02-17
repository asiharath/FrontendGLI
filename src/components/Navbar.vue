<template>
  <div class="navbar">
    <ul class="left-content">
      <li>
        <router-link to="/home"><font-awesome-icon icon="home"/></router-link>
        </li>
    </ul>
  </div>
</template>

<script>

export default {
  name: "navbar",
  
  data() {
    return {
      isLoggedIn: false,
    }
  }
};
</script>

<style lang="css" scoped>
 .navbar {
   box-shadow: 0 0 3px rgba(0,0,0,0.25);
   transition: background-color 0.3s ease-in-out;
   height: 5%;
 }
 .left-content {
   display: flex;
   justify-content: left;
   align-items: center;
   height: 100%;
 }
  li {
    list-style: none;
  }
</style>