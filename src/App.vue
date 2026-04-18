<script setup>
import { ref } from "vue";

let num = ref(0);
</script>

<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-primary">
    <div class="container-fluid">
      <router-link class="navbar-brand" to="/">
        <img
          src="/src/assets/homeicon.png"
          alt="Logo"
          width="30"
          height="24"
          class="d-inline-block align-text-top"
        />
        PokeMaster
      </router-link>
      <router-link class="navbar-brand" to="/"></router-link>
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
            <router-link class="nav-link" to="/">Home</router-link>
          </li>
          <li class="nav-item">
            <router-link class="nav-link" to="/about">Sobre</router-link>
          </li>
        </ul>
      </div>
    </div>
  </nav>

  <!--CONTENT-->
  <div class="main">
    <router-view></router-view>
  </div>

  <footer class="bg-primary text-light">
    <div class="fw-bold">Construído por Felipe Martins</div>
  </footer>
</template>

<style>
footer {
  position: fixed;
  bottom: 0;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 56px;
}
</style>
