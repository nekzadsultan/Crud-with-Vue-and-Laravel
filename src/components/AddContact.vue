<template>
  <div class="container">
    <div class="row">
      <div class="col-md-6">
        <div class="alert alert-danger" v-if="errors.length">
          <ul class="mb-0">
            <li v-for="(error,index) in errors" :key="index">
              {{error}}
            </li>
          </ul>
        </div>
        <form @submit.prevent="saveContact">
          <fieldset>
            <div class="form-group">
              <div class="form-group">
                <label for="exampleInputEmail1">Name</label>
                <input type="text" class="form-control" v-model="contact.name" id="exampleInputEmail1" aria-describedby="emailHelp" placeholder="Enter Name">
              </div>
              <div class="form-group">
                <label for="exampleInputEmail1" class="mt-4">Email address</label>
                <input type="email" class="form-control" v-model="contact.email" id="exampleInputEmail1" aria-describedby="emailHelp" placeholder="Enter email">
              </div>
              <div class="form-group">
                <label for="exampleInputEmail1" class="mt-4">Designation</label>
                <input type="text" class="form-control" id="exampleInputEmail1" v-model="contact.designation" aria-describedby="emailHelp" placeholder="Enter Designation">
              </div>        
              <div class="form-group">
                <label for="exampleInputEmail1" class="mt-4">Contact No</label>
                <input type="text" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" v-model="contact.contact_no" placeholder="Enter Contact No">
              </div>
            </div>
            <button class="btn btn-success mt-4">Save</button>
          </fieldset>
        </form>
      </div>
    </div> 
  </div>
</template>
<script>
import axios from 'axios'

export default {
        name :"AddContact",
        data () {
          return {
            contact:{},
            name:'',
            email:'',
            designation:'',
            contact_no:'',
            errors : []
          }
        },
        methods : {
          async saveContact(){
            this.errors =[]
            if( !this.contact.name ){
              this.errors.push('Name is required')
            }
            if( !this.contact.email ){
              this.errors.push('email is required')
            }
            if( !this.contact.designation ){
              this.errors.push('designation is required')
            }
            if( !this.contact.contact_no ){
              this.errors.push('Contact No is required')
            }
            if(!this.errors.length){
              let formData=new FormData();
              formData.append('name',this.contact.name)
              formData.append('email',this.contact.email)
              formData.append('designation',this.contact.designation)
              formData.append('contact_no',this.contact.contact_no)
              let url = "http://php81.example.com/laravel_api/public/api/save_contact"
              await axios.post(url,formData).then(response => {
                console.log(response)
                if(response.status == 200){
                  this.contact.name=''
                  this.contact.email=''
                  this.contact.designation=''
                  this.contact.contact_no=''

                  alert(response.data.message)
                }
              }).catch(error =>{this.errors.push(error)})
             
            }
            
          }
        }

}
</script>