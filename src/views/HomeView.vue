<template>
  <div class="home">
    <Characters></Characters>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import Characters from '@/components/Characters.vue'

export default {
  name: 'home',
  components: {
    HelloWorld,
    Characters
  }
}
</script>
