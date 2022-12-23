<script lang="ts">
import ComicCatalog from './ComicCatalog.vue'
// import Cloudworld from './CloudWorld.vue'
import { defineComponent } from '@nuxtjs/composition-api'
import 'normalize.css'

export default defineComponent({
  components: {
    ComicCatalog
    // Cloudworld
  },
  setup() {
    
  },
})
</script>

<template>
  <div>
    <ComicCatalog />
    <!-- <Cloudworld /> -->
  </div>
</template>
