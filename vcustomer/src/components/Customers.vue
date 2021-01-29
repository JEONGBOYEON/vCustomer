<template>
  <div class="customers container">
    <Alert v-if="alert" :message="alert"></Alert>
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
        <tr v-for="(customer,index) in customers" :key="customer.id">
          <td>{{customer.first_name}}</td>
          <td>{{customer.last_name}}</td>
          <td>{{customer.email}}</td>
          <td><button class="btn btn-default" @click="customerDetail(index)">Detail</button></td>
        </tr>
      </tbody>
    </table>
  </div>
</template>


<script>
import Alert from './Alert.vue'
export default {
  name: 'customers',
  components: {Alert},
  data () {
    return {
      alert:'',
      customers: [
        {
          id:1,
          first_name:"boyeon",
          last_name:"jeong",
          email:"boyeon.jeong@bes.com",
          phone:"010-1234-1234",
          city:"Seoul",
          state:"f",
          address:"alQkdi"
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
    },
    customerDetail(index){
      console.log();
      this.$router.push({
        name:'CustomerDetails', 
        params:{
          customer:this.customers[index]
        }
      });
      // this.$router.push({name:"CustomerDetails",params:{customer:this.customers[index]}});
    }
  },
  created: function(){
    // this.fetchCustomers();
    if(this.$route.params.customer){
      this.customers.push(this.$route.params.customer);
      this.alert=this.$route.params.alert;
    }
  }
}
</script>
