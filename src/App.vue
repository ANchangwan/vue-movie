<script>
import data from './assets/movies.js';
import Navbar from "@/components/Navbar.vue";
import Modal from "@/components/Modal.vue";
import Movies from "@/components/Movies.vue";
import Event from "@/components/Event.vue";
import SearchBar from "@/components/SearchBar.vue";


export default {
  name: 'App',
  data() {
    return {
      isModal: false,
      data,
      data_temp:[...data], // 영화 데이타 사본
      selectedMovie:0,
      text:[
          'Netflix 강렬한 운명의 드라마, 경성 크리처',
          '디즈니 100주년 기념작, 위치'
      ],
      eventTextNum:0
    };
  },
  methods: {
    increaseLike(id) {
      this.data.find(movie => {
        if (movie.id === id){
          movie.like += 1;
        }
      })
    },
    searchMovie(title){
      this.data_temp = this.data.filter(movie => {
        return movie.title.includes(title);
      })
    },
    showAllMovie(){
      return this.data_temp =[...this.data];
    }
  },
  components: {
    Navbar,
    Modal,
    Movies,
    Event,
    SearchBar,
  },
  mounted() {
    console.log('mounted');
    setInterval(() => {
      this.eventTextNum += 1;
      if(this.text.length - 1 < this.eventTextNum) this.eventTextNum = 0;
    },3000)
  }
};
</script>

<template>
  <Navbar />
  <Event :text="text[eventTextNum]"/>
  <SearchBar :data="data_temp"  @searchMovie="searchMovie($event)" />

  <p>
    <button @click ="showAllMovie" >전체보기</button>
  </p>
  <div class="movie_info">
    <Movies
        @increaseLike="increaseLike($event)"
        @openModal="isModal = true; selectedMovie=$event"
        :data="data_temp" />
    <Modal
        :data="data"
        :isModal="isModal"
        :selectedMovie="selectedMovie"
        @closeModal="isModal=false"
    />
  </div>
</template>

<style>
*{
  box-sizing: border-box;
  margin: 0;

}
body{
  width: 500px;
  margin: 0 auto;
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
  .movie_info {
    padding: 5px;
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
  .subtitle{
    width: 100%;
    background: gray;
    height: 30px;
    padding: 5px;
    color: white;
  }

</style>
