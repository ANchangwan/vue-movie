<script>
export default {
  name: 'App',
  data() {
    return {
      isModal: false,
      data: [
        {
          title: "노량",
          year: 2023,
          category: "액션, 드라마",
          textRed: "color:red",
          like:0,
          imgUrl:"/public/assets/노량.jpeg",
        },
        {
          title: "아쿠아 맨",
          category: "action, fantasy", // 오타 수정
          year: 2023,
          like:0,
          imgUrl: "/public/assets/아쿠아맨.jpg",
        }
      ]
    };
  },
  methods: {
    increasLike(i) {
      this.data[i].like += 1;
    },
  }
};
</script>

<template>
  <h1>영화 정보</h1>
  <div v-for="(item, index) in data" :key="index" class="item">
    <figure>
      <img :src="`${item.imgUrl}`" :alt="item.title" />
    </figure>
    <div class="info">
      <h1 class="title">{{ item.title }}</h1>
      <div>
        <span>장르 :</span>
        <span>{{ item.category }}</span>
      </div>
      <div class="likeit" v-if="true">
        <span>{{ item.year }}</span>
        <div  class="btn__like-col">
          <button @click="increasLike(index)">좋아요</button>
          <span>{{ item.like }}</span>
          <p>
            <button @click="isModal=true">상세보기</button>
          </p>
        </div>
      </div>

    </div>
  </div>
  <div class="modal" v-if="isModal">
    <div class="inner">
      <h3>Detail</h3>
      <p>영화 상세보기</p>
      <button @:click="isModal=false">닫기</button>
    </div>
  </div>
</template>

<style>
  body{
    width: 758px;
    margin: 0 auto;
    padding: 20px;
    position:relative;

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
    width: 80%;
    height: 15%;


  }

</style>
