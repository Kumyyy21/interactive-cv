// === FILE: src/components/Navbar.vue ===
<script setup>
import { ref } from 'vue';

const isMenuOpen = ref(false);

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};

// Tutup menu saat link diklik (opsional, tapi disarankan untuk UX yang baik)
const closeMenu = () => {
  isMenuOpen.value = false;
};
</script>

<template>
  <header class="bg-white shadow-md sticky top-0 z-50 animate-fade-in">
    <nav class="container mx-auto px-6 py-4 flex justify-between items-center">
      <div class="text-2xl font-bold text-gray-800">Hibatulhaqqi Qasthalani Rifqi</div>

      <div class="md:hidden">
        <button @click="toggleMenu" class="text-gray-600 hover:text-blue-500 focus:outline-none focus:text-blue-500 p-2 rounded">
          <svg v-if="!isMenuOpen" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"></path>
          </svg>
          <svg v-else class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
          </svg>
        </button>
      </div>

      <ul class="hidden md:flex space-x-6">
        <li><a href="#profil" class="text-gray-600 hover:text-blue-500 transition-all">Profil</a></li>
        <li><a href="#pendidikan" class="text-gray-600 hover:text-blue-500 transition-all">Pendidikan</a></li>
        <li><a href="#skill" class="text-gray-600 hover:text-blue-500 transition-all">Skill</a></li>
        <li><a href="#proyek" class="text-gray-600 hover:text-blue-500 transition-all">Proyek</a></li>
        <li><a href="#kontak" class="text-gray-600 hover:text-blue-500 transition-all">Kontak</a></li>
      </ul>
    </nav>

    <Transition name="slide-fade">
      <div v-if="isMenuOpen" class="md:hidden">
        <ul class="flex flex-col space-y-4 px-6 py-4 bg-white shadow-lg border-t border-gray-200">
          <li><a @click="closeMenu" href="#profil" class="block text-gray-600 hover:text-blue-500 transition-all py-2">Profil</a></li>
          <li><a @click="closeMenu" href="#pendidikan" class="block text-gray-600 hover:text-blue-500 transition-all py-2">Pendidikan</a></li>
          <li><a @click="closeMenu" href="#skill" class="block text-gray-600 hover:text-blue-500 transition-all py-2">Skill</a></li>
          <li><a @click="closeMenu" href="#proyek" class="block text-gray-600 hover:text-blue-500 transition-all py-2">Proyek</a></li>
          <li><a @click="closeMenu" href="#kontak" class="block text-gray-600 hover:text-blue-500 transition-all py-2">Kontak</a></li>
        </ul>
      </div>
    </Transition>
  </header>
</template>

<style scoped>
/* Animasi Slide-Fade untuk menu mobile */
.slide-fade-enter-active,
.slide-fade-leave-active {
  transition: all 0.3s ease-out;
}

.slide-fade-enter-from,
.slide-fade-leave-to {
  transform: translateY(-20px); /* Mulai dari sedikit di atas */
  opacity: 0; /* Mulai dengan transparan */
}
</style>
