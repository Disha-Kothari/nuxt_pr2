<template>
<header>
      <nav class="navbar navbar-expand-lg bg-light">
      <a role="link" href="/" aria-label="Home" title="">
    <img src="../assets/img/Netflix-Logo.png" alt="Netflix" class="img-fluid" /></a >
    <h1>Netflix</h1>
        <div class="container-fluid ">
            <div class="collapse navbar-collapse" id="navbarNav">
            <ul class="navbar-nav">
                <li class="nav-item">
                    <NuxtLink to="#" class="nav-link">Home</NuxtLink>
                </li>
                <li class="nav-item">
                    <NuxtLink to="/users" class="nav-link">Users</NuxtLink>
                </li>
                <li class="nav-item">
                    <NuxtLink to="/users/create" class="nav-link">Create User</NuxtLink>
                </li>
                <li class="nav-item">
                    <NuxtLink to="/users/694/edit" class="nav-link">Edit User</NuxtLink>
                </li>
            </ul>
            </div>
        </div>
    </nav>
    <!-- <nav>
        <ul>
            <li><NuxtLink to="/users/create">Titles</NuxtLink></li>
            <li><NuxtLink to="/users/create">Credits</NuxtLink></li>
        </ul>
    </nav> -->
</header>
</template>
<style scoped>
header {
  line-height: 1.5;
  background-color: #FFF;
  color:#777;
  width: 100vw;
}
ul {
  padding-left: 150px;
  margin: 6px 0;
  width: 100vw;
}
ul li{
    display: inline-block;
    margin-left: 35px;
}
.logo {
  display: block;
  margin: 0 auto 2rem;
  width:50px;
  height:50px;
  object-fit: contain;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
