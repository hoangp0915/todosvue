<template>
            <div class="panel panel-primary">
            <div class="panel-heading">
              <h3>Danh sách User</h3>
            </div>
            <div class="panel-body">
                <table class="table table-dark table-hover">
                <thead>
                  <tr>
                    <th>#</th>
                    <th>Firstname</th>
                    <th>Lastname</th>
                    <th>Email</th>
                    <th width="150">Option</th>
                  </tr>
                </thead>
                <tbody>
                  <tr v-for="(customer,n) in customers">
                    <td>{{n + 1}}</td>
                    <td>{{customer.firstName}}</td>
                    <td>{{customer.lastName}}</td>
                    <td>{{customer.email}}</td>
                    <td>
                      <a class="btn btn-info" href=""><i class="glyphicon glyphicon-edit"></i></a>
                      <button @click="removeCustomer(n)" class="btn btn-danger" href=""><i class="glyphicon glyphicon-trash"></i></button>
                    </td>
                  </tr>
                </tbody>
              </table>
            </div>
          </div>
</template>

<script>
export default {
  name: 'About',
  data () {
    return {
      customers: [],
    }
  },
  mounted() {
        this.customers = JSON.parse(localStorage.getItem('customers'));
  },
  methods:{
  	removeCustomer(x) {
      this.customers.splice(x, 1);
      const parsed = JSON.stringify(this.customers);
      localStorage.setItem('customers', parsed);
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
