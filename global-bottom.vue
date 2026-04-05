<template>
  <footer
    v-if="$nav.currentLayout !== 'cover' && $nav.currentLayout !== 'end'"
    class="slide-footer absolute bottom-0 left-0 right-0 flex items-center justify-between px-8 py-2"
  >
    <span class="footer-title">
      LVMH Tech Hackathon — Integration / MuleSoft
    </span>
    <span>
      {{ $nav.currentPage }} / {{ $nav.total }}
    </span>
  </footer>
</template>
