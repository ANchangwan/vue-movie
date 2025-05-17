<template>
  <nav>
    <ul>
      <li><a href="#">Home</a></li>
      <li><a href="#">Movies</a></li>
      <li><a href="#">About</a></li>
    </ul>
  </nav>
</template>

<script>
  export default {
    name: 'NavbarComponent',
  }
</script>

<style>
  nav{
    padding: 20px;
    width: 100%;
    background-color: black;
  }
  nav>ul{
    display: flex;
    gap: 1rem;
    text-decoration: none;
    justify-content: center;
  }
  nav>ul>li>a{
    text-decoration: none;
    color:white;

  }
</style>