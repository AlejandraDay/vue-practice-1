<template>
  <div class="home" id="Home">
    <br />
    <br />
    <br />
    <img alt="Vue logo" src="../assets/logo.jpg" />
    <br />
    <!--img alt="Vue logo" src="../assets/logo.png" /-->
    <br />
    <br />
    <label>Search by Name or Description: </label>
    <input v-model="searchNameDesc" />
    <label> Select a Category: </label>
    <select v-model="selecteCategory">
      <option>Books</option>
      <option>Magazines</option>
      <option>Newspapers</option>
      <option>Others</option>
      <option>All</option>
    </select>
    <Library
      :columns="columns"
      :filterNameDesc="searchNameDesc"
      :filterCategory="selecteCategory"
    >
    </Library>
    <br />
    <br />
  </div>
</template>

<script>
// @ is an alias to /src
import Library from "@/components/Library.vue";

export default {
  name: "Home",
  components: {
    Library
  },
  data() {
    return {
      //msg: "Welcome to Your Library",
      searchNameDesc: "", //name or description
      selecteCategory: "All", //category
      columns: ["code", "name", "description", "category"]
    };
  }
};
</script>
<style src="./home.css" scoped></style>
