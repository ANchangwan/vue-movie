<script>


export default {
  name: "MoviesComponents",
  props: {
    data: Array,
    isModal:Boolean,
  }
}
</script>

<template>
  <div class="movie_info">
    <h1>영화 정보</h1>
    <div v-for="(item) in data" :key="item.id" class="item">
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
            <button @click="$emit('increaseLike',item.id)" >좋아요</button>
            <span>{{ item.like }}</span>
            <p>
              <button @click="$emit('openModal', item.id)">상세보기</button>
            </p>
          </div>
        </div>

      </div>

    </div>
  </div>
</template>

<style scoped>

</style>