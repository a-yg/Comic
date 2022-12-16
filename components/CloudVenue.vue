<script>
import { defineComponent } from '@nuxtjs/composition-api'
import { ref } from 'vue'

export default defineComponent({
  props: ["data"],
  setup(props) {
    const selectVenue = ref("accusamus beatae ad facilis cum similique qui sunt") 

    const onClick = (id) => {
      console.log(id, 'id')
      const params = props.data.find(obj => id == obj.id)
      selectVenue.value = params.title
      console.log(selectVenue.value, 'value')
    }

    return {
      onClick,
      selectVenue,
    }
  },
})
</script>

<template>
  <div class="container">
    <p class="position"><img src="https://winter2022.vketcloud.com/img/top/icon_pin.svg"><span>選択している会場:</span>
    <span><p class="select">{{selectVenue}}</p></span>
    </p>
    <ul>
    <li class="ticketItems" v-for="i in data" :key="i.i" @click="onClick(i.id)">
      <img class="baseimg" src="../assets/img/ticket_base.png" alt="">
      <div class="ticket">
        <div class="img">
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
</template>

<style scoped>
.container {
  width: 465px;
  background-color: rgba(0,0,0,0.5);
  position: absolute;
  right: 0;
  padding-bottom: 32px;
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
.img > img {
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
</style>