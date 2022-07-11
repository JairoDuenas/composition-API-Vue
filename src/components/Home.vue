<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <div>{{ text }}</div>
  <div>{{ obj }}</div>
</template>

<script>
import { ref, reactive } from "vue";

export default {
  setup() {
    const text = ref("Hola Vue");
    const obj = reactive({ counter: 0 });

    setInterval(() => obj.counter++, 700);
    return {
      text,
      obj,
    };
  },
};
</script>