<script>
import { defineComponent } from '@nuxtjs/composition-api'
import ComicHeader from './ComicHeader.vue'
import ComicCatalog from './ComicCatalog.vue'

export default defineComponent({
  components: {
    ComicHeader,
    ComicCatalog,
  },
  setup() {
    
  },
})
</script>

<template>
  <div>
    <ComicHeader />
    <ComicCatalog />
  </div>
</template>

<style scoped>
hr {
  margin: 0;
}
</style>