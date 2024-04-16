<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>

    <div class="wrapper">
      <nav>
        <RouterLink to="/">Первое ТЗ</RouterLink>
        <RouterLink to="/about">Второе ТЗ</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>
<style scoped>
.wrapper {
  padding: 20px 0;
}
</style>
