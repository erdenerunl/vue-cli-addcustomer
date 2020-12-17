<template>
  <div>
    <h1>Customer</h1>
    <hr />
    <div class="container">
      <input
        type="text"
        class="form-group"
        placeholder="First name..."
        v-model="formData.firstName"
      />
      <input
        type="text"
        class="form-group"
        placeholder="Last name..."
        v-model="formData.lastName"
      />
      <input
        type="text"
        class="form-group"
        placeholder="Email..."
        v-model="formData.email"
      />
      <button class="btn btn-primary" :class="addDisabled" @click="addCustomer">Add Customer</button>
    </div>
    <customer-list :customers="customers" />
  </div>
</template>

<script>
import CustomerList from './components/CustomerList.vue'

export default {
  name: 'App',
  components: {
    CustomerList
  },
  data() {
    return {
      formData: {
        firstName: "",
        lastName: "",
        email: "",
      },
      customers: [],
    };
  },
  methods: {
    clearForm() {
      this.formData = {
        firstName: "",
        lastName: "",
        email: "",
      };
    },
    addCustomer() {
      this.customers.push({
        id: this.customers.length + 1,
        ...this.formData,
      });
      console.log(this.customers);
      this.clearForm();
    },
  },
  computed : {
    addDisabled(){
      return {
        'disabled' : this.customers.firstName === '' || 
        this.customers.lastName === '' || 
        this.customers.email === ''
      }
    }
  }
}
</script>

<style>
h1{
  margin: 20px 60px;
}
input {
  width: 100%;
  margin-bottom: 5px;
}
button{
  width: 100%;
}
</style>
