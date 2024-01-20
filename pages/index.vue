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
  <nav>
    <NuxtLink to="/second">Second_Page</NuxtLink>
  </nav>
  <header>
    <img src="/image.webp" height="512" :style="styleObject" />
  </header>
  <div class="content">
    <h2>Steps to reproduce:</h2>
    <p>
      - The parallax effect will break if the page rerenders some part. You can
      test this by editing "THIS" word in code.<br />
      - It will also break if you build the project and run it on preview or
      production server.
    </p>
    <h2>Temporary fix:</h2>
    <p>
      - It will be fixed if you reload the page (only on dev server).<br />
      - It will also be fixed if you switch pages and come back.<br />
    </p>
    <h2>Real fix:</h2>
    <p>The actual fix is in the `index.vue` file commented out in line 15.</p>
    <h2>For scrolling:</h2>
    <p s>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Vel velit
      mollitia quidem incidunt nemo iusto sequi blanditiis, dolore quisquam eos
      reiciendis atque consequuntur ducimus assumenda at! Reiciendis magnam quas
      accusamus soluta fuga commodi maiores. Earum necessitatibus iste optio
      nisi officia porro facilis qui, ut ad quod itaque, harum, consequuntur
      molestiae. Id reprehenderit vitae nisi culpa quas qui, odio dicta.
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
.content {
  max-width: 48rem;
  margin: 0 auto;
}
p {
  font-family: monospace;
}
[s] {
  max-width: 4rem;
}
</style>
