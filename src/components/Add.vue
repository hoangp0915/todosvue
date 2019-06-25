<template>
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
                  <button type="submit" class="btn btn-primary" @click="addCustomer()" >Submit</button>
                </div>
              </form>
           </div>
          </div>
</template>

<script>
export default {
  name: 'About',
  props: {
  	vnewCustomer:{
  		type: Array,
  	}
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
