<script setup lang="ts">
import ClickCounter from './components/ClickCounter.vue';
import ItemList from './components/ItemList.vue';
import WelcomeMessage from './components/WelcomeMessage.vue'
</script>
//npm run devはtodolist-mehm8128に移動してから実行しないとファイルが見つけられずエラー
<template>
  <main>
    <WelcomeMessage msg="Webエンジニアになろう講習会へようこそ" />
    <ClickCounter />
    <ItemList />
  </main>
</template>

<style scoped>
main {
  padding: 2rem;
}
</style>
