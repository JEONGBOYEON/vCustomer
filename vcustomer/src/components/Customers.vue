<template>
  <div class="customers container">
    <h1 class="page-header">Manage Customers</h1>
    <table class="table table-striped">
      <thead>
        <tr>
          <th>First Name</th>
          <th>Last Name</th>
          <th>Email</th>
          <th></th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="customer in customers" :key="customer.id">
          <td>{{customer.first_name}}</td>
          <td>{{customer.last_name}}</td>
          <td>{{customer.email}}</td>
          <td></td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'Customers',
  data () {
    return {
      customers: [
        {
          id:1,
          first_name:"boyeon",
          last_name:"jeong",
          email:"boyeon.jeong@bes.com"
        },
        {
          id:2,
          first_name:"surim",
          last_name:"lee",
          email:"surim.lee@bes.com"
        },
        {
          id:3,
          first_name:"bomi",
          last_name:"jeong",
          email:"bomi.jeong@bes.com"
        },
      ]
    }
  },
  methods: {
    fetchCustomers(){
      this.$http.get('http://slimapp/api.customers').then(function(response){console.log(response.body)});
    }
  },
  created: function(){
    // this.fetchCustomers();
    if(this.$route.params.customer){
      this.customers.push(this.$route.params.customer);
    }else{
      console.log("null");
    }
  }
}
</script>
