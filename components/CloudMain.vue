<script>
import { defineComponent } from '@nuxtjs/composition-api'
import { onMounted, ref } from 'vue'
import axios from 'axios'
import CouldVenue from '../components/CloudVenue.vue'

export default defineComponent({
  components: {
    CouldVenue,
  },
  setup() {
    const data = ref([])
    // const img1 = ref("")
    // const img2 = ref("")
    onMounted( async() => {
      const url = "https://jsonplaceholder.typicode.com/photos"
      try {
        const res = await axios.get(url)
        data.value = res.data.slice(0, 8)
        console.log(data.value, 'data')
      } catch (error) {
        console.log("get失敗")
      }
    })

    

    switch(data.value.id) {
      case 0:
        cosole.log('1111')
        // img1.value = "../assets/img/bg_01.jpg"
        // img2.value = "../assets/img/bg_02.jpg"
        break
      case 1:
        cosole.log('2222')
        // img1.value = "../assets/img/bg_01_disneyplus.jpg"
        // img2.value = "../assets/img/bg_02_disneyplus.jpg"
        break
    }
    // const imgs = ref([
    //   {img: require("../assets/img/bg_01.jpg")},
    //   {img: require("../assets/img/bg_02.jpg")}
    //   ])
    // console.log(imgs.value.length, 'img!!!')


    // javascriptで背景自動アニメーション
    // const img_src = ref()
    // img_src.value = [require("../assets/img/bg_01.jpg"), require("../assets/img/bg_02.jpg")]
    // console.log(img_src.value.length, 'img!!!')
    // let num = -1

    // const slide_time = () => {
    //   if(num == img_src.value.length) {
    //     num == 0
    //   } else {
    //     num++
    //   }
    //   document.getElementById("slide_img").src = img_src[num]
    // }
    // setInterval(slide_time, 2000)
    return {
      data,
      // img1,
      // img2,
      // img_src,
      // num,
      // slide_time
    }
  },
})
</script>

<template>
  <div class="main">
    <!-- <div class="items" v-for="i in imgs" :key="i.i">
      <img class="img" :src="i.img"> -->

      <!-- <img class="img" id="slide_img" :src="require(img1)" alt="">
      <img class="img" :src="require(img2)"  alt=""> -->

      <img class="img" id="slide_img" src="../assets/img/bg_01_disneyplus.jpg" alt="">
      <img class="img" src="../assets/img/bg_02_disneyplus.jpg"  alt="">
      <div class="message">
        <img src="../assets/img/catchcopy_jp.png" alt="">
      </div>
    <!-- </div> -->
    <CouldVenue :data="data"/>
  </div>
</template>

<style scoped>
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
