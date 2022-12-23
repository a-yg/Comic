<script>
import { computed, defineComponent, onMounted, ref } from '@nuxtjs/composition-api'
import 'bootstrap-icons/font/bootstrap-icons.css'

export default defineComponent({
  setup() {
    const check = ref("aa")
    const saleCheck = ref(true)
    const text = ref("出展物のキーワードを入力")

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
    // 検索機能
    const keyword = ref()
    const items = props.items
    const filterKeyword = computed(() => {
      for(let i in items.value) {
        let item = items.value[i]
        if(item.world.indexOf(keyword.value) !== -1) {
          items.value.push(items)
        }
      }
    })
    
    return {
      check,
      saleCheck,
      switchSale,
      text,
      items,
      keyword,
      filterKeyword
    }
  },
})
</script>

<template>
  <div class="class">
    <div class="radio">
      <input type="radio" value="aa" id="aa" v-model="check" @change="switchSale">
      <label for="aa">出展物</label>
      <input type="radio" value="bb" id="bb" v-model="check" @change="switchSale">
      <label for="bb">サークル</label>
    </div>
    <div class="search">
      <input type="text" :placeholder="text" v-model="keyword">
      <button><i class="bi bi-search"></i></button>
    </div>
    <div class="select">
      <label for="">絞り込み</label>
      <select name="" id="">
        <option selected>---Select---</option>
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
    <div class="check" v-if="saleCheck">
      <input type="checkbox" id="check" class="checkbox">
      <label for="check">販売している<br>出展物のみ</label>
    </div>
    <div class="button">
      <a href="">♡ お気に入り</a>
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
    z-index: 4;
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
  right: -5px;
  top: 0;
  height: -webkit-fill-available;
  width: 60px;
  background: #1845c2;
  border-radius: 5px;
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

.check > label {
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
</style>