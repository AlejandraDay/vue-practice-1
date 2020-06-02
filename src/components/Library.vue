<template>
  <div>
    <!-- span>Name or Description</span>
    <br />
    <br />
    <input v-model="nameInput" placeholder="Search" /-->
    <br />
    <br />
    <table id="table">
      <thead>
        <tr>
          <th :key="columnkey.code" v-for="columnkey in columns" class="tables">
            {{ columnkey }}
          </th>
        </tr>
      </thead>
      <tbody>
        <tr :key="item.data" v-for="item in filteredList">
          <td :key="key" v-for="key in columns">
            {{ item[key] }}
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import data from "./data.json";
export default {
  name: "HelloWorld",
  methods: {},
  props: {
    // data: Array,
    columns: Array,
    filterNameDesc: String,
    filterCategory: String
    // msg: String
  },
  data() {
    return {
      selecteCategory: "",
      radioSelect: "",
      radioOptionA: "",
      list: data
    };
  },
  computed: {
    filteredList() {
      var nameDesc = this.filterNameDesc.toUpperCase();
      var category = this.filterCategory.toUpperCase();
      const categoryList =
        this.filterCategory === "All" || this.filterCategory === ""
          ? this.list
          : this.list.filter(item => item.category.toUpperCase() === category);
      return this.filterNameDesc === ""
        ? categoryList
        : this.list.filter(
            item =>
              item.name.toUpperCase().includes(nameDesc) ||
              item.description.toUpperCase().includes(nameDesc)
          );
    }
  }
};
</script>
<style src="../views/home.css" scoped></style>
