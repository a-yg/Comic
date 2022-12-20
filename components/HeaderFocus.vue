<script>
import { defineComponent, onMounted, ref, useRouter } from '@nuxtjs/composition-api'
import axios from 'axios'

export default defineComponent({
  setup() {
    const data = ref()
    const detail = ref()
    onMounted(async() => {
      const url = "https://jsonplaceholder.typicode.com/photos"
      try {
        const res = await axios.get(url)
        data.value = res.data.slice(0, 3)
        console.log(data.value, "data")
      } catch(e) {
        console.log("get失敗")
      }

      try {
        const res2 = await axios.get(url)
        detail.value = res2.data.slice(0, 8)
        console.log(detail.value, "detail")
      } catch(e) {
        console.log("get失敗")
      }
    })
    const isOpen = ref(false)
    const mouseover = () => {
      isOpen.value = true
    }
    const mouseleave = () => {
      isOpen.value = false
    }

    const router = useRouter()
    const enterpriseClick = (id) => {
      console.log(id, 'id')
      const params = data.value.find(obj => id == obj.id)
      console.log(params.id, "param")
      router.push({path: `/world/${params.id}`})
    }
    const generalClick = (id) => {
      console.log(id, 'id')
      const params = detail.value.find(obj => id == obj.id)
      console.log(params.id, "param")
      router.push({path: `/world/${params.id}`})
    }
    
    return {
      data,
      detail,
      isOpen,
      mouseover,
      mouseleave,
      enterpriseClick,
      generalClick
    }
  },
})
</script>

<template>
    <li class="item" @mouseover="mouseover" @mouseleave="mouseleave">
        <router-link to="/ComicCatalog">
          <span>CATALOG</span>
          <span class="textsub">カタログ</span>
        </router-link>

        <ul class="subitems" :class="{isOpen}">
          <div class="enterprise">
            <div class="enworld">
            <div><p>企業ワールド</p></div>
            <div class="list">
              <li v-for="i in data" :key="i.i" class="subitem" @click="enterpriseClick(i.id)">
                <img :src="i.url"><p>{{i.title}}</p>
              </li>
            </div>
            </div>
          </div>
          <div class="general">
            <p>一般ワールド</p>
            <div class="list">
              <li v-for="i in detail" :key="i.i" class="subitem" @click="generalClick(i.id)">
                <img :src="i.url"><p>{{i.title}}</p>
              </li>
            </div>
          </div>
        </ul>
    </li>
</template>

<style scoped>
a {
  color: black;
  text-decoration: none;
  display: flex;
  flex-direction: column;
  font-size: 22px;
  text-align: center;
}
ul {
  list-style-type: none;
}
.subitem {
  text-align: center;
}
.textsub {
  font-size: 12px;
}

.subitems, .list {
  display: flex;
  justify-content: left;
  gap: 8px;
  padding: 0;
}
.subitems {
  display: none;
  position: absolute;
  top: 80px;
  left: 0;
  background-color: #f5f5f5;
  width: 100%;
}
.subitem > img {
  width: 100%;
}
.subitem > p {
  font-size: 10px;
}
.enterprise {
  /* text-align: left; */
  width: 50%;
  padding: 0 0 0 200px;
}
.general {
  text-align: left;
  width: 50%;
  padding: 0 200px 0 0;
}
.enworld > .list {
  width: 70%;
}
.enworld {
  width: 83%;
  display: flex;
  flex-direction: column;
  align-items: end;
}
.enworld > div {
  width: inherit;
}
.enworld > div > p {
  padding-left: 75px;
}
.general > .list {
  display: flex;
  flex-wrap: wrap;
  width: 70%;
}
.general > .list > .subitem {
  width: 20%;
}
.isOpen {
  display: flex;
}
.subitem:hover {
  filter: opacity(70%);
  cursor: pointer;
}

</style>