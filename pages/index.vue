<script setup lang="ts">
import type { CSSProperties } from "vue";
import { onMounted, onBeforeUnmount, ref } from "vue";

const styleObject = ref<CSSProperties>({});

const handleScroll = () => {
  window.requestAnimationFrame(() => {
    const scrollTop = window.scrollY || document.documentElement.scrollTop;

    // broken original:
    styleObject.value.transform = `translate3d(0, ${scrollTop / 2}px, 0)`;

    // replace with fix:
    // styleObject.value = { transform: `translate3d(0, ${scrollTop / 2}px, 0)` };
  });
};

onMounted(() => {
  window.addEventListener("scroll", handleScroll);
});

onBeforeUnmount(() => {
  window.removeEventListener("scroll", handleScroll);
});
</script>

<template>
  <NuxtLink to="/second">Second_Page</NuxtLink>
  <header>
    <img src="/image.webp" height="512" :style="styleObject" />
  </header>
  <div class="content">
    <h2>For scrolling:</h2>
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Vel velit
      mollitia quidem incidunt nemo iusto sequi blanditiis, dolore quisquam eos
      reiciendis atque consequuntur ducimus assumenda at! Reiciendis magnam quas
      accusamus soluta fuga commodi maiores. Earum necessitatibus iste optio
      nisi officia porro facilis qui, ut ad quod itaque, harum, consequuntur
      molestiae. Id reprehenderit vitae nisi culpa quas qui, odio dicta.
      Praesentium magni quae perspiciatis nulla deleniti eligendi quisquam
      suscipit quo eveniet, minima optio laboriosam eaque, voluptatibus omnis
      fugit tempora ea sint aliquam eum libero! Numquam doloremque
      necessitatibus itaque excepturi ut odio consequatur enim sapiente ipsa
      ullam. Enim laboriosam tempora sit? Cumque?
    </p>
  </div>
</template>

<style>
header {
  height: 512px;
  overflow: hidden;
  display: flex;
  justify-content: center;
  box-shadow: inset 0 0 2rem 0 #000;
  padding: 2rem;
}

.content p {
  max-width: 4rem;
}
</style>
