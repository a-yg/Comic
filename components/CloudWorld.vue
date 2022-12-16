<script>
import { defineComponent, ref, onMounted, useRouter, useRoute, watch } from '@nuxtjs/composition-api'
import axios from 'axios'

export default defineComponent({
  setup() {
    const router = useRouter();
    const route = useRoute();
    const data = ref([])
    const img1 = ref(require("../assets/img/bg_01.jpg"))
    const img2 = ref(require("../assets/img/bg_02.jpg"))
    const worldUrl = ref("https://winter2022.vketcloud.com/general/main.html?worldid=jrcentral&multi=1&roomid=pub_lz4yXcxiNVeot2SRf2")
    const selectVenue = ref("accusamus beatae ad facilis cum similique qui sunt") 
    const workId = ref()
    
    onMounted( async() => {
      const url = "https://jsonplaceholder.typicode.com/photos"
      try {
        const res = await axios.get(url)
        data.value = res.data.slice(0, 8)
        handleChangeImage();
        console.log(data.value, 'data')
      } catch (error) {
        console.log("get失敗")
      }
    })

    // クリック時にqueryの変更
    const onClick = (id) => {
      const params = data.value.find(obj => id == obj.id)
      selectVenue.value = params.title
      switch(params.id) {
        case 1:
          router.push({path: '/', query:{ work_id:'disneyplus' }})
          break
        case 2:
          router.push({path: '/', query:{ work_id:'beams' }})
          break
      }
    }
    
    // queryに対して画像の変更
    const handleChangeImage = () => {
      console.log(route.value.query.work_id, 'route.value.query.work_id');
      workId.value = route.value.query.work_id
      switch(workId.value) {
        case 'disneyplus': {
          img1.value = require("../assets/img/bg_01_disneyplus.jpg")
          img2.value = require("../assets/img/bg_02_disneyplus.jpg")
          worldUrl.value = "https://winter2022.vket.com/world"

          break
        }
        case 'beams': {
          img1.value = require("../assets/img/bg_01_beams.jpg")
          img2.value = require("../assets/img/bg_02_beams.jpg")
          worldUrl.value = "https://winter2022.vket.com/uc/official"
          break
        }
      }
    }

    // queryの変更を監視する
    watch(route, () => {
      console.log(route, "route@@@@@@")
      handleChangeImage()
  })
    
    return {
      data,
      img1,
      img2,
      onClick,
      workId,
      selectVenue,
      worldUrl
    }
  },
})
</script>

<template>
<div>
  <div class="main">
      <img class="img" id="slide_img" :src="img1" alt="">
      <img class="img" :src="img2"  alt="">
      <div class="message">
        <img src="../assets/img/catchcopy_jp.png" alt="">
      </div>

      <div class="alart">
          <p>
            <a href="https://account.vket.com/terms#realtime-communication">利用規約</a>と
            <a href="https://account.vket.com/terms#privacy">プライバシーポリシー</a>に同意します
          </p>
        <div class="prosCons">
          <a :href="worldUrl" class="pros">同意する</a><br>
          <router-link to="/ComicTop" class="cons">同意しない</router-link>
        </div>
      </div>
  </div>

  <div class="container">
    <p class="position"><img src="https://winter2022.vketcloud.com/img/top/icon_pin.svg"><span>選択している会場:</span>
    <span><p class="select">{{selectVenue}}</p></span>
    </p>
    <ul>
    <li class="ticketItems" v-for="i in data" :key="i.i" @click="onClick(i.id)">
      <img class="baseimg" src="../assets/img/ticket_base.png" alt="">
      <div class="ticket">
        <div class="image">
          <img :src="i.url" alt="">
        </div>
        <div class="detail">
          <p class="url">{{ i.url }}</p>
          <p class="title">{{ i.title }}</p>
        </div>
      </div>
    </li>
    </ul>
  </div>
</div>
</template>

<style scoped>
.container {
  width: 465px;
  background-color: rgba(0,0,0,0.5);
  position: absolute;
  right: 0;
  top: 0;
  padding-bottom: 32px;
  opacity: 1;
}
ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
  height: 100%;
}
.position {
  padding: 6px 20px 0px 38px;
  /* font-weight: bold; */
  font-size: 13px;
  color: #fff;
  background-color: rgba(0,0,0,0.6);
  margin: 0px 0px 8px 0;
}
.position > span {
  vertical-align: super;
  margin-left: 5px;
}
.ticketItems {
  position: relative;
  padding: 2px 30px; 
  opacity: 0.7;
  transition: all 0.3s ease;
}
.ticketItems:hover {
  opacity: 1;
  cursor: pointer;
  /* left: 3%; */
  transform: translate(5px);
}
.ticket {
  display: flex;
  position: absolute;
  top: 26px;
  left: 35px;
}
.baseimg {
  width: 385px;
}
.image > img {
  width: 66px;
}
.url {
  font-size: 0.5vw;
    font-weight: bold;
    color: #88ADFF;
    margin: 5px;
}
.title {
  font-size: 0.8vw;
  font-weight: bold;
  color: #1845C2;
  margin: 0;
}
.detail {
  margin-left:10px;
  width: 235px;
}
.select {
  font-size: 12px;
}
.alart {
  width: 400px;
  padding: 40px 40px 30px;
  background: rgba(255, 255, 255, 0.7);
  box-shadow: 0px 0px 20px rgb(0 0 0 / 20%);
  position: absolute;
  top: 345px;
  left: 391px;
  opacity: 0.9;
}
.alart > p > a, .alart > p {
  margin: 0;
  color: #333;
  text-align: center;
}
.prosCons {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 48px;
}
.prosCons > a {
  color: #fff;
  text-decoration: none;
  padding: 16px;
  font-size: 24px;
  font-weight: bold;
  line-height: 1.3;
  color: #fff;
  text-align: center;
  border-radius: 8px;
  transition: all 0.2s ease;
  width: 50%;
}
.pros {
  background-color: blue;
}
.cons {
  background-color: gray;
}



.main {
	position: relative;
	height: 910px;
}
.img {
	position: absolute;
	width: 100%;
  height: 100%;
	opacity: 0;
	animation: change-img-anim 4s infinite;
}
.img:nth-of-type(1) {
	animation-delay: 2s;
}
.img:nth-of-type(2) {
	animation-delay: 2s;
}
@keyframes change-img-anim {
	0%{ opacity: 0;}
	70%{ opacity: 1;}
	90%{ opacity: 1;}
	100%{ opacity: 0;}
}
.message {
  position: absolute;
  top: 120px;
  left: 360px;
}
.message > img {
  width: 488px;
}
</style>
