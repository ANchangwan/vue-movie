<template>
  <nav>
    <a href="#">Home</a>
    <a href="#">Movies</a>
    <a href="#">About</a>
  </nav>
</template>

<script>
export default {
  name: "NavbarComponent",
};
</script>

<style>
nav {
  background-color: black;
  padding: 20px;
  display: flex;
  justify-content: center;
  align-items: center;
  gap:1rem;
}


nav > a {
  text-decoration: none;
  color: white;
}
</style>
