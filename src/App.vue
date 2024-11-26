<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>
    <div class="wrapper">
      <nav>
        <RouterLink to="/" class="button" aria-label="Aller à l'accueil">
          Accueil
        </RouterLink>
        <RouterLink to="/trashed" class="button" aria-label="Aller à la corbeille">
          Corbeille
        </RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>
header {
  @apply flex justify-center py-4 bg-gray-800 text-white;
}

.wrapper {
  @apply w-full max-w-screen-md mx-auto px-4;
}

nav {
  @apply flex justify-between;
}

.button {
  @apply px-4 py-2 rounded-lg bg-gray-700 hover:bg-gray-600 transition-colors;
}

.button.router-link-active {
  @apply bg-gray-600 font-bold;
}
</style>
