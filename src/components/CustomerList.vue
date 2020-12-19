<template>
  <div>
    <div class="container d-flex flex-column align-items-center">
      <input
        v-if="customers.length > 0"
        type="text"
        class="mt-4 w-50"
        v-model="searchText"
        placeholder="Search customer..."
      />
      <table class="table my-4" v-if="searchContent.length > 0">
        <thead>
          <th>First Name</th>
          <th>Last Name</th>
          <th>Email</th>
          <th class="text-center">View</th>
        </thead>
        <tbody>
          <tr v-for="customer in searchContent" :key="customer.id">
            <td>{{ customer.firstName }}</td>
            <td>{{ customer.lastName }}</td>
            <td>{{ customer.email }}</td>
            <button class="btn btn-outline-primary">View</button>
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
  computed: {
    searchContent() {
      return this.searchText === ""
        ? this.customers
        : this.customers.filter((c) => c.firstName.includes(this.searchText) || 
        c.lastName.includes(this.searchText) ||
        c.email.includes(this.searchText));
    },
  },
};
</script>


<style scoped>
</style>