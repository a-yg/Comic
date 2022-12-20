<script lang="ts">
import ComicHeader from './ComicHeader.vue'
import ComicCatalog from './ComicCatalog.vue'
import { defineComponent } from '@nuxtjs/composition-api'
import 'normalize.css'

export default defineComponent({
  components: {
    ComicHeader,
    ComicCatalog
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
