<script>
import { computed, defineComponent, onMounted, ref, useRouter } from '@nuxtjs/composition-api'
import ComicHeader from './ComicHeader.vue'
import ComicSearch from '../components/ComicSearch.vue'
import axios from 'axios'

import 'bootstrap-icons/font/bootstrap-icons.css'

export default defineComponent({
  components:{
    ComicHeader,
    ComicSearch
  },
  setup() {
    const check = ref("aa")
    const saleCheck = ref(true)
    const text = ref("出展物のキーワードを入力")

    const currentImageIndex =ref(0)
    const items = ref([
      {
        id: 1,
        bgimg : require("../assets/img/paris.jpg"),
        title: "企業 | PC（VRChat）",
        world: "パラリアルパリ",
        genre: "1"
      },
      {
        id: 2,
        bgimg: require("../assets/img/nagoya.jpg"),
        title: "企業 | PC（VRChat）",
        world: "パラリアル名古屋",
        genre: "1"
      },
      {
        id: 8,
        bgimg: require("../assets/img/nagoya.jpg"),
        title: "企業 | PC（VRChat）",
        world: "aaa",
        genre: "2"
      },
      {
        id: 9,
        bgimg: require("../assets/img/nagoya.jpg"),
        title: "企業 | PC（VRChat）",
        world: "bbb",
        genre: "2"
      },
      {
        id: 10,
        bgimg: require("../assets/img/nagoya.jpg"),
        title: "企業 | PC（VRChat）",
        world: "ccc",
        genre: "3"
      },
      {
        id: 11,
        bgimg: require("../assets/img/nagoya.jpg"),
        title: "企業 | PC（VRChat）",
        world: "ddd",
        genre: "4"
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

    // ラジオボタンによって表示変更
    const switchSale = () => {
      console.log(check.value, "check")
      if (check.value == "bb") {
        saleCheck.value = false
        text.value = "サークルのキーワードを入力"
      } else {
        saleCheck.value = true
        text.value = "出展物のキーワードを入力"
      }
    }

    // 検索フォームとセレクトボックス
    const searchKeyword = ref('');
    const selectedFilterItem = ref('');
    const filteredItems = ref(items.value);
    const searchItem = () => {
      console.log(searchKeyword.value, "searchKeyword.value")
      console.log(selectedFilterItem.value, "selectedFilterItem.value")
      if (!searchKeyword.value && !selectedFilterItem.value) return

      // if(searchKeyword.value && selectedFilterItem.value) {
      //   filteredItems.value = items.value.filter((item) => {
      //     return item.world.includes(searchKeyword.value);
      //   }).filter((item) => {
      //     return item.title.includes(searchKeyword.value)
      //   })
      //   return;
      // }
      
      if(searchKeyword.value) {
        filteredItems.value = items.value.filter((item) => {
          return item.world.includes(searchKeyword.value);
        })
      }

      if(selectedFilterItem.value) {
        filteredItems.value = items.value.filter((item) => {
          return item.genre.includes(selectedFilterItem.value);
        })
      }
    }

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

    const data = ref([])
    onMounted(async() => {
      const url = "https://jsonplaceholder.typicode.com/photos"
      const res = await axios.get(url)
      data.value = res.data.slice(0, 15)
      console.log(data, "catalogdata")
    })
    // const onMoveHitCircle = () => {
    //   router.push({path: 'hitcircle'})
    // }
 
    
    return {
      check,
      saleCheck,
      switchSale,
      text,
      items,
      items2,
      searchKeyword,
      selectedFilterItem,
      filteredItems,
      searchItem,
      // onMoveHitCircle,

      onClick,
      onText1Click,
      onText2Click,
      currentImageUrl,
      imageMouseOver,
      data
    }
  },
})
</script>

<template>
<div>
<ComicHeader style="box-shadow: none"/>
<ComicSearch :data="data"/>
<!-- @searchItems="onMoveHitCircle" -->
<div class="class">
    <div class="radio">
      <input type="radio" value="aa" id="aa" v-model="check" @change="switchSale">
      <label for="aa">出展物</label>
      <input type="radio" value="bb" id="bb" v-model="check" @change="switchSale">
      <label for="bb">サークル</label>
    </div>
    <div class="search">
      <input type="text" :placeholder="text" v-model="searchKeyword" @keydown.enter="searchItem">
      <button @click="searchItem"><i class="bi bi-search"></i></button>
    </div>
    <div class="select">
      <label for="">絞り込み</label>
      <select name="item" id="item" v-model="selectedFilterItem" @change="searchItem">
        <option value="">---Select---</option>
        <option disabled="disabled" value="0">---キャラクター---</option>
        <option value="1">人間</option>
        <option value="2">亜人</option>
        <option value="3">魔物</option>
        <option disabled="disabled" value="0">---装飾品---</option>
        <option value="4">衣装</option>
        <option value="5">髪型</option>
        <option value="6">アクセサリー</option>
      </select>
    </div>
    <div class="check">
      <div v-if="saleCheck">
        <input type="checkbox" id="check" class="checkbox">
        <label for="check">販売している<br>出展物のみ</label>
      </div>
    </div>
    <div class="button">
      <a href="">♡ お気に入り</a>
    </div>
  </div>


<div class="bgimg" :style="{ backgroundImage: 'url(' + currentImageUrl.bgimg + ')' }">
  <div class="container">
    <div class="stamp">
      <a href="https://winter2022.vket.com/stamprally">
      <img src="../assets/img/stamprally.jpg">
      </a>
    </div>
    <div>
      <ul class="world-item">
          <li class="items" v-for="item in filteredItems" :key="item.id" @click="onClick(item.id)">
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
</div>
</template>

<style scoped>
.class {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 30px;
    background-color: #f5f5f5;
    box-shadow: 0 3px 6px rgb(0 0 0 / 15%);
    position: sticky;
    top: 80px;
    z-index: 3;
    height: 60px;
}

.radio > label {
  font-size: 14px;
  color: #333;
  margin-right: 8px;
}
.radio > input {
  /* radioボタンのサイズ変更 */
  transform: scale(1.3);
  cursor: pointer;
}

.search {
  position: relative;
  width: 320px;
}
.search > input {
  width: 290px;
  height: 25px;
  padding: 8px 16px;
}
.search > button {
  position: absolute;
  right: -7px;
  top: 0;
  height: -webkit-fill-available;
  width: 60px;
  background: #1845c2;
  border-radius: 5px;
  border: none;
}

.select > label {
  font-size: 14px;
  color: #333;
}
.select > select {
  width: 280px;
  height: 44px;
  font-size: 14px;
  padding: 8px 16px;
  appearance: none;
}

.check {
  display: flex;
  justify-content: end;
  align-items: center;
  gap: 8px;
  width: 105px;
  position: relative;
}
/* checkbox初期化 */
input[type='checkbox'] {
  appearance: none;
  outline: none;

  display: block;
  text-align: center;
  cursor: pointer;
}
/* checkboxのデザイン */
input[type='checkbox']::before {
  display: block;
  position: absolute;
  top: 6px;
  left: 0;
  content: '';

  width: 14px;
  height: 14px;
  background: transparent;
  border: 3px solid #757575;
  border-radius: 3px;
}
/* checkboxmのチェックのデザイン */
input[type='checkbox']::after {
  display: block;

  content: '';
  position: absolute;
  left: 5px;
  top: 7px;

  width: 6px;
  height: 10px;
  border-right: 4px solid blue;
  border-bottom: 4px solid blue;
  transform: rotate(45deg);

  opacity: 0;
}
/* チェックするとチェックマークの透明化を解除 */
input[type='checkbox']:checked::after {
  opacity: 1;
}

.check > div > label {
  color: #333;
  font-size: 13px;
  line-height: 1.2;
  white-space: pre-wrap;
}


.button {
    border: 2px solid #999;
    border-radius: 8px;
    display: block;
    height: 40px;
    background-color: #fff;
    display: flex;
    align-items: center;
    padding: 0 10px;
    margin-left: 70px;
}
.button > a {
  text-decoration: none;
  color: #333;
  font-size: 14px;
}





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