<template>
  <div id="app">
    <Terminal/>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import Terminal from '~/components/Terminal.vue';

export default Vue.extend({
  components: { Terminal },
  name: 'IndexPage'
})
</script>
