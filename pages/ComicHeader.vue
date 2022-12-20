<script>
import { defineComponent } from '@nuxtjs/composition-api'
import HeaderFocus from '../components/HeaderFocus.vue'
import 'bootstrap-icons/font/bootstrap-icons.css'
import 'normalize.css'

export default defineComponent({
  components: {
    HeaderFocus
  },
  setup() {
    
  },
})
</script>

<template>
  <header>
    <nav class="nav">
      <a href="https://winter2022.vket.com/" class="img"><img src="../assets/img/logo-2022.png"></a>
      <ul class="category">
        <li class="item"><a href="https://winter2022.vket.com/about"><span>ABOUT</span><span class="textsub">概要</span></a></li>
        <li class="item"><a href="https://winter2022.vket.com/access"><span>ACCESS</span><span class="textsub">来場方法</span></a></li>
        <HeaderFocus />
        <li class="item"><a href=""><span>EVENT</span><span class="textsub">イベント</span></a></li>
        <li class="item"><a href="https://winter2022.vket.com/contact"><span>CONTACT</span><span class="textsub">お問い合わせ</span></a></li>
        <li class="item"><router-link to="/cloudworld"><span>VKETCLOUD</span><span class="textsub">メタバース空間</span></router-link></li>
      </ul>
      <ul class="log">
        <li class="button">
          <svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 32 32" class="icon" data-v-ee3557c6="" data-v-7df525e2=""><defs data-v-ee3557c6="" data-v-7df525e2=""><style data-v-ee3557c6="" data-v-7df525e2="">.a{fill:#707070;}</style></defs><path d="M18,2A16,16,0,1,0,34,18,16.006,16.006,0,0,0,18,2Zm0,4.8a4.8,4.8,0,1,1-4.8,4.8A4.794,4.794,0,0,1,18,6.8Zm0,22.72a11.521,11.521,0,0,1-9.6-5.152c.048-3.184,6.4-4.928,9.6-4.928,3.184,0,9.552,1.744,9.6,4.928A11.521,11.521,0,0,1,18,29.52Z" transform="translate(-2 -2)" class="a" data-v-ee3557c6="" data-v-7df525e2=""></path></svg>
          <p>ログイン</p></li>
        <li class="language"><p class="text">Language :</p>
        <i class="bi bi-1-circle"></i>
        <i class="bi bi-2-circle-fill"></i>
        </li>
      </ul>
    </nav>
  </header>
</template>

<style scoped>
* {
  margin: 0;
  padding: 0;
}
header {
  background-color: #fff;
  box-shadow: 0 3px 6px rgb(0 0 0 / 20%);
  position: sticky;
  top: 0;
  z-index: 4;
}
ul {
  list-style-type: none;
}
a {
  color: black;
  text-decoration: none;
}
.nav {
  display: flex;
  padding: 0 32px;
}
.category {
  display: flex;
  justify-content: center;
  flex: 1;
}
.item > a {
  display: flex;
  flex-direction: column;
  font-size: 22px;
  text-align: center;
  padding: 0 10px;
}
.item > a:hover {
  color: #1845c2;
}
.item {
  display: flex;
  padding: 0 10px;
  align-items: center;
}

.textsub {
  font-size: 12px;
}

.item:hover {
visibility: visible; /*ホバー後、アンダーラインを可視化する*/
border-bottom: 2px solid #1845c2
}


.img > img {
  width: 120px;
}

.log {
  display: flex;
  align-items: center;
}
.button {
  border: 2px solid #1845c2;
  border-radius: 6px;
  color: #1845c2;
  font-size: 14px;
  margin-right: 16px;
  padding: 8px 16px;
  display: flex;
  align-items: center;
}
.button:hover {
  cursor: pointer;
  background-color: #1845c2;
  color: #fff;
}
.button > svg {
  height: 20px;
  margin-right: 8px;
  width: 20px;
}
.button > .icon > .a {
  fill: #1845c2;
}
.button > .icon > .a:hover {
  fill: #fff;
}
.text {
  color: #333;
}
.language {
  display: flex;
}
.language > i {
  margin: 0 3px;
}
.language > i:hover {
  cursor: pointer;
}
</style>