<template>
  <div class="event" v-show="isOpen">
    <span>{{text}}</span>
    <button @click="isOpen = false">X</button>
  </div>
</template>

<script>
  export default {
    name: "EventComponent",
    props:{
      text:String,
      isEventOption:Boolean,
    },
    data(){
      return {
        isOpen: true
      }
    }
  }
</script>

<style>
  .event{
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 100%;
    padding: 10px;
    background: gray;
    color: white;
  }
  .event button{
    margin: 0;
  }
</style>