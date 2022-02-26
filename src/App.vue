<template>

<!-- nav -->
<div class="wrapper">
  <nav class="navbar navbar-expand-lg navbar-light bg-light">
  <div class="container-fluid">
    <router-link class="navbar-brand" to="/">userCRM</router-link>
    <div id="navbarNav">
      <ul class="navbar-nav">
        <li class="nav-item">
          <router-link class="nav-link" to="/">Home</router-link>
        </li>
        <li class="nav-item">
          <router-link class="nav-link" to="/users">Users</router-link>
        </li>
        <li class="nav-item">
          <router-link class="nav-link" to="/about">About</router-link>
        </li>
    
      </ul>
    </div>
  </div>
</nav>


<div class="container">
  <router-view/>
</div>
</div>

  


</template>

<style>

</style>
