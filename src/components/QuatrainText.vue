<template>
  <div v-if="visible" class="quatrain">
    <p>{{ text }}</p>
  </div>
</template>

<script setup>
import { defineProps } from "vue";

defineProps({
  text: String,
  visible: Boolean,
});
</script>

<style scoped>
.quatrain {
  margin-bottom: 1.5rem;
  font-size: 1.8rem;
}

@media (max-width: 768px) {
  .quatrain {
    font-size: 1.4rem;
  }
}

@media (max-width: 480px) {
  .quatrain {
    font-size: 0.9rem;
  }
}
@media (max-width: 380px) {
  .quatrain {
    font-size: 0.8rem;
  }
}
@media (min-width: 2560px) {
  .quatrain {
    font-size: 2.5rem;
  }
}
@media (min-width: 3840px) {
  .quatrain {
    font-size: 3.5rem;
  }
}

@media (min-width: 7680px) {
  .quatrain {
    font-size: 7rem;
  }
}
</style>
