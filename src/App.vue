<template>
  <div id="app">
    <app-header/>
    <!-- <router-view/> -->
  </div>
</template>

<script>
import AppHeader from '@/components/Header';

export default {
  name: 'app',
  components: { AppHeader },
};
</script>

<style lang="scss" src="./styles/base.scss"></style>
