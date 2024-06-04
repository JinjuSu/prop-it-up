<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-light">
    <div class="container-fluid">
      <a class="navbar-brand" href="#">Prop-it-out</a>
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarSupportedContent"
        aria-controls="navbarSupportedContent"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav me-auto mb-2 mb-lg-0">
          <li class="nav-item">
            <router-link to="/">
              <a class="nav-link active" aria-current="page"
                >Home</a
              ></router-link
            >
          </li>
        </ul>
        <div class="d-flex">
          <div>
            <router-link to="/signup"
              ><button class="btn btn-primary">Sign up</button></router-link
            >
          </div>
          <div>
            <router-link to="/login">
              <button class="btn btn-outline-primary">
                Log in
              </button></router-link
            >
          </div>
          <div>
            <button class="btn btn-outline-primary">Log out</button>
          </div>
        </div>
      </div>
    </div>
  </nav>
</template>
<script>
export default {
  name: "Navbar",
  components: {},
};
</script>
