<script>
import data from './assets/movies.js';
import Navbar from "@/components/Navbar.vue";
import Modal from "@/components/Modal.vue";
import Movies from "@/components/Movies.vue";


export default {
  name: 'App',
  data() {
    return {
      isModal: false,
      data,
      selectedMovie:0,
    };
  },
  methods: {
    increaseLike(i) {
      this.data[i].like += 1;
    },
  },
  components: {
    Navbar,
    Modal,
    Movies,
  }
};
</script>

<template>
  <Navbar />

  <div class="movie_info">
    <Movies
        @increaseLike="increaseLike($event)"
        @openModal="isModal = true; selectedMovie=$event" :data="data" />
    <Modal
        :data="data"
        :isModal="isModal"
        :selectedMovie="selectedMovie"
        @closeModal="isModal=false"
    />
  </div>
</template>

<style>
  body{
    width: 538px;
    margin: 0 auto;
    position:relative;
    box-sizing: border-box;
  }
  h1, h2, h2 {
    margin-bottom: 1rem;
  }
  p{
    margin-bottom: 1rem;
  }
  button {
    margin-right: 10px;
    margin-top: 1rem;
  }
  .item{
    display: flex;
    border: 1px solid black;
    width:100%;
    padding: 1rem;
    margin-bottom:20px;
  }
  .item figure{
    width: 30%;
    margin-right: 1rem;
  }
  .item img{
    width:100%;
  }
  .item .info{
    width: 100%;
    gap:1rem;
  }

  li{
    list-style: none;
  }
  .modal{
    position: fixed;
    background: rgba(0, 0, 0, 0.7);
    left: 0;
    top: 0;
    width: 100%;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .modal .inner{
    background: white;
    padding: 10px;
    border-radius: 10px;
    width: 350px;
    height: 150px;
  }

</style>
