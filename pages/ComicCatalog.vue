<script>
import { computed, defineComponent, onMounted, ref, useRouter } from '@nuxtjs/composition-api'
import axios from 'axios'

export default defineComponent({
  setup() {
    const currentImageIndex =ref(0)
    const items = ref([
      {
        id: 1,
        bgimg : require("../assets/img/paris.jpg"),
        title: "企業 | PC（VRChat）",
        world: "パラリアルパリ"
      },
      {
        id: 2,
        bgimg: require("../assets/img/nagoya.jpg"),
        title: "企業 | PC（VRChat）",
        world: "パラリアル名古屋"
      }
    ])
    const items2 = ref([
      {
        bgimg: require("../assets/img/cosmotravel.jpg"),
        title: "一般 | PC（VRChat）",
        world: "Cosmotravel Elevator",
        item: {
          id: 3,
          text1: "Alpha-E",
        },
        item2: {
          id: 4,
          text2: "T-Omega",
        }
      },
      {
        bgimg: require("../assets/img/wunderkammer.jpg"),
        title: "一般 | PC（VRChat）",
        world: "コルト夫人のヴンダーカンマー",
        item: {
          id: 5,
          text1: "脅威の目録",
        },
        item2: {
          id: 6,
          text2: "不可思議名鑑",
        }
      },
    ])

    // クリック時にid取って画面遷移
    const router = useRouter()
    const onClick = (id) => {
      console.log(id, 'aa')
      const params = items.value.find(obj => id == obj.id)
      console.log(params.id, "id")
      router.push({path:`/world/${params.id}`})
    }
    const onText1Click = (id) => {
      console.log(id, "@@@")
      const params = items2.value.find(obj => id == obj.item.id)
      const param = items2.value.find(obj => id == obj.item2.id)
      console.log(params, "id111111")
      router.push({path:`/world/${params.item.id}`})
      router.push({path:`/world/${param.item2.id}`})
    }
    const onText2Click = (id) => {
      console.log(id, "@@@")
      const params = items2.value.find(obj => id == obj.item2.id)
      console.log(params, "id111111")
      router.push({path:`/world/${params.item2.id}`})
    }

    // マウスオーバー時にbgimage変更
    const currentImageUrl = computed(() => {
      console.log(currentImageIndex.value, "currentImageIndex.value")
      return items2.value[currentImageIndex.value]
    })
    const imageMouseOver = (index) => {
      console.log(index, 'index')
      currentImageIndex.value = index
    }

    
    return {
      items,
      items2,
      onClick,
      onText1Click,
      onText2Click,
      currentImageUrl,
      imageMouseOver
    }
  },
})
</script>

<template>
<div class="bgimg" :style="{ backgroundImage: 'url(' + currentImageUrl.bgimg + ')' }">
  <div class="container">
    <div class="stamp">
      <a href="https://winter2022.vket.com/stamprally">
      <img src="../assets/img/stamprally.jpg">
      </a>
    </div>
    <div>
      <ul class="world-item">
          <li class="items" v-for="item in items" :key="item.item" @click="onClick(item.id)">
            <img :src="item.bgimg">
            <p class="title">{{item.title}}</p>
            <p class="world"><span>{{item.world}}</span></p>
          </li>
      </ul>
      <ul class="world-item">
          <li class="items2" v-for="(i, index) in items2" :key="index" @mouseover="imageMouseOver(index)">
            <img :src="i.bgimg">
            <p class="title">{{i.title}}</p>
            <p class="world"><span>{{i.world}}</span></p>
            <ul>
              <div>
              <li class="text1" @click="onText1Click(i.item.id)"><p>{{i.item.text1}}</p></li>
              <li class="text2" @click="onText2Click(i.item2.id)"><p>{{i.item2.text2}}</p></li>
              </div>
            </ul>
          </li>
      </ul>
    </div>
  </div>
</div>
</template>

<style scoped>
ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
}
.bgimg {
  background-size: cover;
  display: flex;
  justify-content: center;
  position: relative;
  z-index: 0;
  overflow: hidden;
}
.bgimg:before{
  content: '';
  background: inherit;
  -webkit-filter: blur(6px);
  -moz-filter: blur(6px);
  -o-filter: blur(6px);
  -ms-filter: blur(6px);
  filter: blur(6px);
  position: absolute;
  top: -6px;
  left: -6px;
  right: -6px;
  bottom: -6px;
  z-index: -1;
}
.container {
  background-color: #fff;
  padding: 64px 80px 128px;
  max-width: 1080px;
}
.stamp {
  text-align: center;
  margin-bottom: 30px;
}
.world-item {
  display: flex;
  flex-wrap: wrap;
}
.items, .items2 {
  width: 49%;
  margin: 4px;
  position: relative;
}
.items:hover, .items2:hover {
  cursor: pointer;
}
.items > img, .items2 > img {
  max-width: 100%;
  height: 100%;
}
.title {
  position: absolute;
  top: 0;
  right: 0;
  background-color: #1845c2;
  color: #fff;
  border-radius: 0 0 0 8px;
  margin: 0;
  font-size: 15px;
  font-weight: 300;
  padding: 4px 10px;
  z-index: 8;
}
.items2 > .title {
  background-color: #54bed4;
}
.world {
  position: absolute;
  bottom: 0;
  width: 100%;
  height: 16%;
  text-align: center;
  background-color: hsla(0,0%,100%,.65);
  border-top: 1px solid #333;
  color: #333;
  text-shadow: 2px 2px 0 #fff, -2px 2px 0 #fff, 2px -2px 0 #fff, -2px -2px 0 #fff;
  font-size: 16px;
  font-weight: 700;
  margin: 0;
  z-index: 8;
  display: flex;
  justify-content: center;
  align-items: center;
}
.text1 {
  position: absolute;
  top: 0;
}
.text2 {
  position: absolute;
  top: 42%;
}
.text1, .text2 {
  color: #333;
  display: block;
  font-size: 18px;
  font-weight: 700;
  position: absolute;
  text-shadow: 2px 2px 0 #fff, -2px 2px 0 #fff, 2px -2px 0 #fff, -2px -2px 0 #fff;
  width: 100%;
  height: 42%;
  background: linear-gradient(270deg,hsla(0,0%,100%,0),80%,hsla(0,0%,100%,.65));
  border-bottom: 1px solid #333;
}
.text1 > p, .text2 > p {
  padding: 5%;
}

.items::before, .text1::before, .text2::before {
  content: '';
  display: block;
  position: absolute;
  top: 0;
  left: 0;
  z-index: 1;
  opacity: .2;
  width: 0%;
  height: 100%;
  /* background-color: rgb(23, 102, 133); */
  background-color: blue;
  transition: .3s;
}
.items:hover::before, .text1:hover::before, .text2:hover::before {
		width:100%;
}
</style>