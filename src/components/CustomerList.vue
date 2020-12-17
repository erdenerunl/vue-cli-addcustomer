<template>
  <div>
    <div class="container">
      <input type="text" class="mt-4" v-model="searchText" placeholder="Search customer...">
      <table class="table my-4">
        <thead>
          <th>First Name</th>
          <th>Last Name</th>
          <th>Email</th>
          <th class="text-center">View</th>
        </thead>
        <tbody>
          <tr v-for="customer in customers" :key="customer.id">
            <td>{{ customer.firstName }}</td>
            <td>{{ customer.lastName }}</td>
            <td>{{ customer.email }}</td>
            <button class="btn btn-outline-primary"> View </button>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  props: ["customers"],

  data() {
    return {
      searchText: "",
    };
  },
};
</script>


<style scoped>
</style>