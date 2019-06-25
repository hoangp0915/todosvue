<template>
  <div class="customers container ">
    <h1 class="page-header text-center">Customers</h1>
    <div class="row" @click="[active = !active, col = !col]" style="margin-bottom: 4px">
      <div class="col-sm-12">
        <button class="btn btn-primary">Thêm User</button>
      </div>
    </div>
      <div class="row">
        <div v-show="active" class="col-sm-4" >
          <div class="panel panel-primary">
            <div class="panel-heading">
              <h3>Thêm User</h3>
            </div>
           <div class="panel-body">
              <form role="form">
                    <div class="panel-body">
                      <div class="form-group">
                        <label for="exampleInputEmail1">First Name</label>
                        <input type="text" v-model="newCustomer.firstName" class="form-control" id="exampleInputEmail1" placeholder="Enter First Name">
                      </div>
                      <div class="form-group">
                        <label for="exampleInputPassword1">Last Name</label>
                        <input type="text" v-model="newCustomer.lastName"  class="form-control" id="exampleInputPassword1" placeholder="Enter Last Name">
                      </div>
                     <div class="form-group">
                        <label for="exampleInputPassword1">Email</label>
                        <input type="email" v-model="newCustomer.email" class="form-control" id="exampleInputPassword1" placeholder="Enter Email">
                      </div>
                      
                    </div>

                    <div class="panel-footer">
                      <button type="submit" class="btn btn-primary" @click="addCustomer" >Submit</button>
                    </div>
                  </form>
           </div>
          </div>
        </div>
        <div  :class="[col ? 'col-sm-12' : 'col-sm-8']">
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

    </div>
  </div>
  </div>
</template>

<script>
export default {
  name: 'Customers',
  data () {
    return {
      customers: [],
      newCustomer: 
      {
        firstName: '',
        lastName: '',
        email: '',
      },
      active: false,
      col: true,
    }
  },
  mounted() {
    if (localStorage.getItem('customers')) {
      try {
        this.customers = JSON.parse(localStorage.getItem('customers'));
      } catch(e) {
        localStorage.removeItem('customers');
      }
    }
  },
  methods:{
    addCustomer() {
      // ensure they actually typed something
      if (!this.newCustomer) {
        return;
      }
      this.customers.push(this.newCustomer);
      this.saveCustomers();
      console.log(this.customers);
      console.log(this.newCustomer);
      this.newCustomer = '';
    },
    removeCustomer(x) {
      this.customers.splice(x, 1);
      this.saveCustomers();
    },
    saveCustomers() {
      const parsed = JSON.stringify(this.customers);
      localStorage.setItem('customers', parsed);
    },
    isActive(){
      this.active = true;
      this.col = false;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
