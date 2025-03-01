<script lang="ts">
import type { NuxtError } from '#app'

export default {
  props:{
    error: Object as () => NuxtError
  },
  setup(props){

  }
}

</script>

<template>
  <div>ee
    <h2>{{ error.statusCode }}</h2>
  
    <div v-for="route in $router.options.routes" :key="route.path" :to="route.path">
      <a :href="route.path" v-if="route.name != 'error'">{{ route.name }}</a>
    </div>

  </div>
</template>