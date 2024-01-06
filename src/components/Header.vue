<template>
      <nav class="navbar navbar-expand-lg navbar-light bg-success">
  <a class="navbar-brand text-light" href="#">{{title}}</a>
  <button class="navbar-toggler " type="button" data-toggle="collapse" data-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
    <span class="navbar-toggler-icon"></span>
  </button>
  <div class="collapse navbar-collapse" id="navbarNav">
    <ul class="navbar-nav">
      <li class="nav-item active">
        <router-link class="nav-link text-light" to="/">Home <span class="sr-on   ly"></span></router-link>
      </li>
      <li class="nav-item">
        <router-link class="nav-link text-light" to="/add_contact">Add Contact</router-link>
      </li>
     
    </ul>
  </div>
</nav>
</template>
<script>
export default {
        name :"Header",
        props : {
            title :String
        }
}
</script>