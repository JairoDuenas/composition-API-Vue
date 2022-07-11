<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <div>Hola</div>
</template>

<script>
import { onMounted } from "vue";

export default {
  setup() {
    onMounted(() => {
      console.log("mounted");
    });
  },
};
</script>