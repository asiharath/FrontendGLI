<template>
  <div class="navbar">
    <router-link to="/"></router-link>
    <Autocomplete placeholder="Search" :search="search"></Autocomplete>
  </div>
</template>

<script>
import Autocomplete from "@trevoreyre/autocomplete-vue";

export default {
  name: "navbar",
  components: {
    Autocomplete
  }
};
</script>