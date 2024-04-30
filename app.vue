<template>
  <div>
    <NuxtLayout :name="layout">
      <button @click="changeLayout">{{ nextLayout }}</button>
     <NuxtPage />
    </NuxtLayout>
  </div>
</template>

<script setup>
  const layouts = {
    default: 'default',
    another: 'another'
  }
  const layout = ref(layouts.default);
  const nextLayout = computed(() => layout.value === layouts.default ? layouts.another : layouts.default);

  const changeLayout = () => {
    layout.value = layout.value === layouts.default ? layouts.another : layouts.default;
  }

</script>

<style>
  .page-enter-active,
  .page-leave-active {
    transition: all 0.3s;
  }

  .page-enter-from,
  .page-leave-to {
    opacity: 0.5;
    filter: grayscale(1)
  }
</style>