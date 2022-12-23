<script>
import { defineComponent, onMounted, ref } from '@nuxtjs/composition-api'
import axios from 'axios'
import 'normalize.css'
import ComicHeader from '../ComicHeader.vue'


export default defineComponent({
  components: {
    ComicHeader
  },
  setup() {
    const data = ref()
    const resNumber = ref()
    onMounted(async() => {
      const url = "https://jsonplaceholder.typicode.com/photos"
      const res = await axios.get(url)
      data.value = res.data.slice(0, 15)
      resNumber.value = data.value.length
      console.log(data, "####")
    })

    return {
      data,
      resNumber
    }
  },
})
</script>

<template>
  <div>
  <ComicHeader />
  <div class="container">
    <div class="searchItem">
      <h1>検索結果総数：{{resNumber}}</h1>
      <ul class="items">
        <li v-for="i in data" :key="i.id">
          <svg data-v-360af93e="" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 31.02 27.03" class="favorite-icon"><defs data-v-360af93e=""><style data-v-360af93e="">.body{fill:none;}.border{fill:#757575;}</style></defs><g data-v-360af93e="" class="body"><path data-v-360af93e="" d="M28.63,2.41c-3.19-3.18-8.35-3.18-11.54,0l-1.57,1.57-1.57-1.57c-3.17-3.2-8.33-3.22-11.53-.05-3.2,3.17-3.22,8.33-.05,11.53,.01,.01,.03,.03,.04,.04l1.57,1.57,11.54,11.52,11.54-11.52,1.57-1.57c3.18-3.17,3.19-8.33,.01-11.51,0,0,0,0-.01-.01Z"></path></g><g data-v-360af93e="" class="border"><path data-v-360af93e="" d="M22.86,2.03c-1.65,0-3.19,.64-4.36,1.8l-1.57,1.57c-.78,.78-2.05,.78-2.83,0l-1.57-1.57c-1.16-1.16-2.71-1.8-4.36-1.8s-3.19,.64-4.36,1.8c-1.16,1.16-1.8,2.7-1.8,4.35s.64,3.18,1.8,4.35l11.7,11.68,11.7-11.68c1.16-1.16,1.8-2.7,1.8-4.35s-.64-3.18-1.8-4.35c-1.16-1.16-2.71-1.8-4.36-1.8m0-2c2.09,0,4.18,.8,5.77,2.39h0c3.19,3.18,3.19,8.34,0,11.52l-13.11,13.09L2.41,13.94C-.78,10.75-.78,5.6,2.41,2.41,5.59-.77,10.76-.77,13.94,2.41l1.57,1.57,1.57-1.57C18.68,.82,20.77,.03,22.86,.03Z"></path></g></svg>
          <div class="name"><img class="human" src="../../assets/img/human.jpeg" alt=""><span>名前</span></div>
          <img :src="i.url" alt="">
          <h2>id:{{i.id}}</h2>
          <div class="position"><img class="img" src="../../assets/img/13320.png"><span>{{i.title}}</span></div>
        </li>
      </ul>
    </div>
  </div>
  </div>
</template>

<style scoped>
ul {
  list-style-type: none;
}
.container {
  background-image: url(../../assets/img/bg-paper.jpg);
  display: flex;
  justify-content: center;
}
.searchItem > h1 {
  margin: 0;
}
.searchItem {
  width: 1280px;
  background-color: #fff;
  padding: 32px 40px 56px;
}
.items {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
  padding: 0;
}
.items > li {
  width: 302px;
  display: block;
  position: relative;
  border: solid 1px #757575;
  border-radius: 7px;
}
.items > li:hover {
  cursor: pointer;
  filter: opacity(70%);
  fill: rgb(248, 148, 164);
}
.items > li > svg {
  position: absolute;
  width: 30px;
  right: 10px;
  top: 10px;
  z-index: 3;
}
.items > li > h2 {
  margin: 51px 20px;
}
.position {
  display: flex;
  align-items: center;
  font-size: 15px;
  margin: 5px;
}
.name {
  position: absolute;
  bottom: 153px;
  left: 15px;
  display: flex;
  align-items: center;
}
.human {
  width: 50px;
  border-radius: 50%;
  margin-right: 10px;
}
/* .items > li > svg:hover {
  fill: rgb(248, 148, 164);
} */
li > img {
  width: 100%;
}
.img {
  width: 30px;
  margin: 10px;
}
</style>