<script>
import { Button } from "@/components/ui/button/index.js";
import { MenuIcon, XIcon } from 'lucide-vue-next';

export default {
  components: { Button, MenuIcon, XIcon },
  data() {
    return {
      isMenuOpen: false,
    };
  },
  methods: {
    toggleMenu() {
      this.isMenuOpen = !this.isMenuOpen;
    },
  },
};
</script>

<template>
  <header class="fixed top-0 left-0 right-0">
    <nav class="container mx-auto px-4 py-4 select-none uppercase tracking-widest">
      <!-- Desktop Menu (lg and above) -->
      <div class="hidden lg:flex items-center justify-center text-sl">
        <a href="/" class="mx-4">Home</a>
        <a href="/merch" class="mx-4">Merch</a>
        <a href="/" class=" text-lg font-bold mx-4">
          <img src="/logo.svg" alt="ЧЕРНЫЕ ОЗЕРА" width="100" height="100" />
        </a>
        <a href="/music" class="mx-4">Music</a>
        <a href="/contact" class="mx-4">Contact</a>
      </div>

      <!-- Tablet Menu (sm to lg) -->
      <div class="hidden sm:flex lg:hidden flex-col items-center py-2 ">
        <a href="/" class="text-lg font-bold mb-2">
          <img src="/logo.svg" alt="ЧЕРНЫЕ ОЗЕРА" width="100" height="100" />
        </a>
        <div class="flex">
          <a href="/" class="mx-4">Home</a>
          <a href="/merch" class="mx-4">Merch</a>
          <a href="/music" class="mx-4">Music</a>
          <a href="/contact" class="mx-4">Contact</a>
        </div>
      </div>

      <!-- Mobile Menu Button (below sm) -->
      <div class="sm:hidden relative flex items-center w-full">
        <Button
            variant="link"
            size="icon"
            @click="toggleMenu"
            aria-label="Открыть меню"
        >
          <MenuIcon />
        </Button>
        <a href="/" class="absolute left-1/2 -translate-x-1/2">
          <img src="/logo.svg" alt="ЧЕРНЫЕ ОЗЕРА" width="50" height="50" />
        </a>
        <div class="w-6"></div>
      </div>

      <!-- Mobile Menu -->
      <div
        v-if="isMenuOpen"
        class="sm:hidden fixed inset-0 z-40 bg/95 backdrop-blur flex items-center justify-center"
      >
        <Button
          variant="link"
          size="icon"
          class="absolute top-4 left-4"
          @click="toggleMenu"
          aria-label="Закрыть меню"
        >
          <XIcon />
        </Button>
        <div class="flex flex-col items-center space-y-8 text-2xl font-medium">
          <a href="/" @click="toggleMenu">Home</a>
          <a href="/merch" @click="toggleMenu">Merch</a>
          <a href="/music" @click="toggleMenu">Music</a>
          <a href="/contact" @click="toggleMenu">Contact</a>
        </div>
      </div>
    </nav>
  </header>
</template>

<style scoped>
header {
  transition: all 0.3s ease-in-out;
}
</style>