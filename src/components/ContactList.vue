<template>
   <div class="container">
        <table class="table table-hover">
            <thead>
                <tr>
                    <th scope="col">#</th>
                    <th scope="col">Name</th>
                    <th scope="col">Email</th>
                    <th scope="col">Designation</th>
                    <th scope="col">Contact No.</th>
                    <th scope="col">Action</th>
                </tr>
            </thead>
            <tbody v-for="(contact,index) in contacts" :key="contact.id">
                <tr class="table-secondary">
                 <th scope="row">{{index+1}}</th>
                 <th scope="row">{{contact.name}}</th>
                 <th scope="row">{{contact.email}}</th>
                 <th scope="row">{{contact.designation}}</th>
                 <th scope="row">{{contact.contact_no}}</th>
                 <th scope="row"><button class="btn btn-danger btn-sm" @click.prevent="deleteContact(contact.id)">Delete</button></th>
                </tr>   
            </tbody>
        </table>
   </div>
</template>
<script>
    import axios from "axios"
export default {

        name : "ContactList",
        data(){
            return {
                contacts : [],
            }
        },
        created(){this.getContacts()},
        methods : {
            async getContacts() {
                let url = "http://php81.example.com/laravel_api/public/api/contact"
                await axios.get(url).then(response => {
                    this.contacts =response.data.contacts
                }).catch(error =>{
                    console.log(error)
                })
            },
            async deleteContact(id){
                let url = `http://php81.example.com/laravel_api/public/api/delete_contact/${id}`
                await axios.delete(url).then(response => {location.reload()})
            }
        },
        mounted(){
            console.log('contact list component mounted')
        }
}
</script>