<script lang="ts">
import CloudTwitter from '../components/CloudTwitter.vue'
// import CloudMain from '../components/CloudMain.vue'
import CloudWorld from '../components/CloudWorld.vue'
import { defineComponent } from '@nuxtjs/composition-api'
import 'normalize.css'

export default defineComponent({
  components: {
    CloudTwitter,
    // CloudMain,
    CloudWorld
  },
  setup() {
    
  },
})
</script>

<template>
  <div>
    <!-- <CloudMain /> -->
    <CloudWorld />
    <CloudTwitter />
  </div>
</template>
