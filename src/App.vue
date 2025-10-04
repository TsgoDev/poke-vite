<script setup></script>

<template>
  <!-- Navbar -->
  <nav class="navbar navbar-expand-lg navbar-dark bg-primary">
    <div class="container-fluid">
      <router-link class="navbar-brand" to="/">PokeVite</router-link>
      <img src="./assets/icon.svg" alt="Bootstrap" width="30" height="40">
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarNav"
        aria-controls="navbarNav"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav">
          <li class="nav-item">
            <router-link class="nav-link" aria-current="page" to="/"
              >Home</router-link
            >
          </li>
          <li class="nav-item">
            <router-link class="nav-link" to="/about">About</router-link>
          </li>
        </ul>
      </div>
    </div>
  </nav>

  <!-- Main -->
  <main class="container">
    <router-view> </router-view>
  </main>

  <!-- Footer -->
   <footer class="bg-primary text-light">
    <div><p>&copy{{ new Date().getFullYear() }} Copyright todos os direitos reservados.</p></div>
   </footer>
</template>

 <style>
    footer {
      position:fixed;
      bottom:0;
      width:100%;
      display:flex;
      align-items:center;
      justify-content:center;
      height:50px;
    }
   </style>
