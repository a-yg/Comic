<script>
import { defineComponent } from '@nuxtjs/composition-api'
import { Tweet } from 'vue-tweet-embed'

export default defineComponent({
  components: {
    Tweet
  },
  setup() {
    
  },
})
</script>

<template>
  <div class="info">
    <div class="note">
      <a class="subnote1" href="https://winter2022.vket.com/access?t=cloud">
      <div class="img"><img src="../assets/img/first.png"></div>
      <div class="subnote2">
        <p class="first">はじめての方へ</p>
        <p class="second">遊び方のご案内</p>
      </div>
      </a>
    </div>
    <div class="twitter">
      <div class="left">
        <div>
          <img svg-inline src="../assets/img/info_logo.svg" alt="">
        </div>
        <a href="https://twitter.com/Virtual_Market_">最新の情報はTwitterをフォロー</a>
      </div>
      <div class="right">
        <div>
          <iframe src="https://syndication.twitter.com/srv/timeline-profile/screen-name/Virtual_Market_?creatorScreenName=Virtual_Market_&dnt=false&embedId=twitter-widget-0&features=eyJ0ZndfdGltZWxpbmVfbGlzdCI6eyJidWNrZXQiOlsibGlua3RyLmVlIiwidHIuZWUiLCJ0ZXJyYS5jb20uYnIiLCJ3d3cubGlua3RyLmVlIiwid3d3LnRyLmVlIiwid3d3LnRlcnJhLmNvbS5iciJdLCJ2ZXJzaW9uIjpudWxsfSwidGZ3X2hvcml6b25fdGltZWxpbmVfMTIwMzQiOnsiYnVja2V0IjoidHJlYXRtZW50IiwidmVyc2lvbiI6bnVsbH0sInRmd190d2VldF9lZGl0X2JhY2tlbmQiOnsiYnVja2V0Ijoib24iLCJ2ZXJzaW9uIjpudWxsfSwidGZ3X3JlZnNyY19zZXNzaW9uIjp7ImJ1Y2tldCI6Im9uIiwidmVyc2lvbiI6bnVsbH0sInRmd19zaG93X2J1c2luZXNzX3ZlcmlmaWVkX2JhZGdlIjp7ImJ1Y2tldCI6Im9uIiwidmVyc2lvbiI6bnVsbH0sInRmd19jaGluX3BpbGxzXzE0NzQxIjp7ImJ1Y2tldCI6ImNvbG9yX2ljb25zIiwidmVyc2lvbiI6bnVsbH0sInRmd190d2VldF9yZXN1bHRfbWlncmF0aW9uXzEzOTc5Ijp7ImJ1Y2tldCI6InR3ZWV0X3Jlc3VsdCIsInZlcnNpb24iOm51bGx9LCJ0Zndfc2Vuc2l0aXZlX21lZGlhX2ludGVyc3RpdGlhbF8xMzk2MyI6eyJidWNrZXQiOiJpbnRlcnN0aXRpYWwiLCJ2ZXJzaW9uIjpudWxsfSwidGZ3X2V4cGVyaW1lbnRzX2Nvb2tpZV9leHBpcmF0aW9uIjp7ImJ1Y2tldCI6MTIwOTYwMCwidmVyc2lvbiI6bnVsbH0sInRmd19kdXBsaWNhdGVfc2NyaWJlc190b19zZXR0aW5ncyI6eyJidWNrZXQiOiJvbiIsInZlcnNpb24iOm51bGx9LCJ0ZndfdmlkZW9faGxzX2R5bmFtaWNfbWFuaWZlc3RzXzE1MDgyIjp7ImJ1Y2tldCI6InRydWVfYml0cmF0ZSIsInZlcnNpb24iOm51bGx9LCJ0Zndfc2hvd19ibHVlX3ZlcmlmaWVkX2JhZGdlIjp7ImJ1Y2tldCI6Im9uIiwidmVyc2lvbiI6bnVsbH0sInRmd19zaG93X2dvdl92ZXJpZmllZF9iYWRnZSI6eyJidWNrZXQiOiJvZmYiLCJ2ZXJzaW9uIjpudWxsfSwidGZ3X3Nob3dfYnVzaW5lc3NfYWZmaWxpYXRlX2JhZGdlIjp7ImJ1Y2tldCI6Im9mZiIsInZlcnNpb24iOm51bGx9LCJ0ZndfdHdlZXRfZWRpdF9mcm9udGVuZCI6eyJidWNrZXQiOiJvbiIsInZlcnNpb24iOm51bGx9fQ%3D%3D&frame=false&hideBorder=false&hideFooter=false&hideHeader=false&hideScrollBar=false&lang=ja&maxHeight=600px&origin=https%3A%2F%2Fwinter2022.vketcloud.com%2F&sessionId=3ba4903975f3f801ae0ff5fa9c95f629a9e7f676&showHeader=true&showReplies=false&siteScreenName=Virtual_Market_&transparent=false&widgetsVersion=a3525f077c700%3A1667415560940" frameborder="0"></iframe>
        </div>
        <div class="rightsub">
          <p>Information in English: <a href="https://twitter.com/EnVket">@EnVket</a></p>
        </div>
    </div>

      <!-- @各Tweetの表示 どっちでも可能 -->
      <!-- <blockquote class="twitter-tweet"><p lang="ja" dir="ltr">/／<br>📢メタバース上で行う世界最大のVRイベント<br>☃『Vket2022 Winter』開催中❗<br>\＼<br><br>🎊2022/12/3(土) - 12/18(日) JST <br><br>🔹クリエイターによるバーチャル空間の祭典❗<br>🔹世界各地から気軽に来場❗<br>🔹出展企業も多数❗<br>🔹入場無料✨<br><br>👉<a href="https://t.co/E2uHV6tSpi">https://t.co/E2uHV6tSpi</a> <a href="https://twitter.com/hashtag/Vket?src=hash&amp;ref_src=twsrc%5Etfw">#Vket</a><a href="https://twitter.com/hashtag/VRChat?src=hash&amp;ref_src=twsrc%5Etfw">#VRChat</a> <a href="https://twitter.com/hashtag/VketCloud?src=hash&amp;ref_src=twsrc%5Etfw">#VketCloud</a> <a href="https://t.co/PlZXqvahsz">pic.twitter.com/PlZXqvahsz</a></p>&mdash; Virtual Market / バーチャルマーケット / Vket | 12/3～18 開催！ (@Virtual_Market_) <a href="https://twitter.com/Virtual_Market_/status/1599265549732966400?ref_src=twsrc%5Etfw">December 4, 2022</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script> -->
      <!-- <tweet id="1599265549732966400"></tweet> -->
    </div>
  </div>
</template>

<style scoped>
a {
  text-decoration: none;
}
.info {
  height: 1000px;
  background-image: url(../assets/img/info_bg.jpg);
  background-position: center;
  background-size: 100% auto;
}
iframe {
  width: 400px;
  height: 600px;
}
.twitter {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 60px;
  margin-top: 100px;
}
.left {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
.left > a {
  font-size: 24px;
  font-weight: bold;
  text-decoration: none;
  color: #fff;
  background-color: #1845C2;
  padding: 17px 40px;
  border-radius: 10px;
  transition: all .5s ease;
}
.left > a:hover {
  background-color: black;
}
.rightsub {
  background-color: rgba(255, 255, 255, 0.7);
  font-size: 14px;
  width: 250px;
  height: 30px;
  text-align: center;
  margin: 24px 0 0 70px;
}
.rightsub > p {
  padding-top: 5px;
}
.rightsub > p > a {
  color: blue;
}


.note {
  display: flex;
  justify-content: center;
}
.subnote1 {
  width: 474px;
  height: 118px;
  display: flex;
  align-items: center;
  justify-content: center;
  border: 1px solid #999;
  border-radius: 10px;
  background-color: #fff;
  gap: 30px;
  margin-top: 80px;
}
.subnote1:hover {
  border: 1px solid green;
  filter: opacity(70%);
}
.img > img {
  width: 65px;
}
.first {
  width: 112px;
  margin-top: 30px;
  margin-bottom: 0;
  padding: 5px 15px;
  color: #fff;
  background-color: #1a8967;
  border-radius: 9999px;
}
.second {
  margin-top: 5px;
  font-size: 32px;
  font-weight: 700;
  color: #1845c2;
}

</style>