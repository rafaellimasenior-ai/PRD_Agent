<template>
  <div class="slide-footer">
    <span class="copyright">© 2026 PRD Writing Skill</span>
    <span class="divider">·</span>
    <span class="page-number">{{ $slidev.nav.currentPage }} / {{ $slidev.nav.total }}</span>
  </div>
</template>

<style scoped>
.slide-footer {
  position: fixed;
  bottom: 1.25rem;
  right: 3rem;
  display: flex;
  justify-content: flex-end;
  align-items: center;
  gap: 0.5rem;
  font-size: 0.65rem;
  font-weight: 400;
  color: #232F3E;
  opacity: 0.35;
  z-index: 10;
  pointer-events: none;
}

.divider {
  opacity: 0.5;
}
</style>
