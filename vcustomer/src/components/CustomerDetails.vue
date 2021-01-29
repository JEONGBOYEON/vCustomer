<template>
  <div class="details container">
    <router-link to="/">Back</router-link>
    <h1 class="page-header">
      {{customer.first_name}} {{customer.last_name}}
      <!-- <span class="pull-right"><button class="btn btn-danger" :click="deleteCustomer">Delete</button></span> -->
    </h1>
    <ul class="list-group">
      <li class="list-group-item"><span class="glyphicon glyphicon-phone" aria-hidden="true"></span>{{customer.phone}}</li>
      <li class="list-group-item"><span class="glyphicon glyphicon-envelope" aria-hidden="true"></span>{{customer.email}}</li>
    </ul>
    <ul class="list-group">
      <li class="list-group-item">{{customer.address}}</li>
      <li class="list-group-item">{{customer.city}}</li>
      <li class="list-group-item">{{customer.state}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'customerDetails',
  data () {
    return {
      customer:{}
    }
  },
  created() {
    if(this.$route.params.customer){
       this.customer=this.$route.params.customer;
    }
  }
}
</script>
