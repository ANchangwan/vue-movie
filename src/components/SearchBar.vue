<script>
export default {
  name: "SearchBarComponent",
  props: {
    data:Array,
  },
  data(){
    return {
      inputText:'',
    }
  },
  watch:{
    inputText(name){
        const findName = this.data.filter(movie=>{
          return movie.title.includes(name);
        });
    }
  }
}
</script>

<template>
  <div class="search-box">
    <input
        type="search"
        @change="
        $emit('searchMovie', $event.target.value);
        inputText= $event.target.value;
        $event.target.value= ''"
        placeholder="검색어 입력"
    />
    <button>검색</button>
  </div>
  <p>{{ inputText }}</p>
</template>

<style scoped>
.search-box{
  padding: 10px;
  display: flex;
  justify-content: center;
}
.search-box input {
  padding: 5px 10px;
}
.search-box button{
  margin:0;
}
</style>