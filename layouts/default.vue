<template>
  <Html
    :class="[
      {
        'is-loaded': homeStore.websiteLoaded,
      },
    ]"
  >
    <Body>
      <div class="default-layout">
        <slot />
      </div>
    </Body>
  </Html>
</template>

<script setup>
import { useHomeStore } from "@/store/home";
const homeStore = useHomeStore();

useSeoMeta({
  title: "Amanita - Fitness Club",
  ogTitle: "Amanita",
  description: "Not a gym. Your evolution.",
  ogDescription: "Not a gym. Your evolution.",
  ogImage: "/images/share.png",
  twitterCard: "summary_large_image",
});

onBeforeMount(() => {
  useLenisScroll();
}),
  onMounted(() => {
    homeStore.changeWebsiteLoaded(true);
  });
</script>

<style lang="scss" scoped>
.default-layout {
  width: 100%;
  height: 100%;
  overflow: hidden;
}
</style>
