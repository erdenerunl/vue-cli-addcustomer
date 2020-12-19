<template>
  <div>
    <h1>Customer</h1>
    <hr />
    <div class="container d-flex  flex-column align-items-center">
      <input
        type="text"
        class="form-group w-50 "
        placeholder="First name..."
        v-model="formData.firstName"
      />
      <input
        type="text"
        class="form-group w-50"
        placeholder="Last name..."
        v-model="formData.lastName"
      />
      <input
        type="text"
        class="form-group w-50"
        placeholder="Email..."
        v-model="formData.email"
      />
      <button class="btn btn-primary w-50" :class="addDisabled" @click="addCustomer">Add Customer</button>
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
      
      this.clearForm();
    },
  },
  computed : {
    addDisabled(){
      return {
        'disabled' : this.formData.firstName === '' || 
        this.formData.lastName === '' || 
        this.formData.email === ''
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
