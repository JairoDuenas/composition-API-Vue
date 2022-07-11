<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <div>{{ text }}</div>
  <div>{{ obj.counter }}</div>
</template>

<script>
import { ref, reactive, watch } from "vue";

export default {
  setup() {
    const text = ref("Hola Vue");
    const obj = reactive({ counter: 0 });

    setInterval(() => obj.counter++, 1000);

    watch(
      () => obj.counter,
      (valor, anterior) => {
        console.log(valor, anterior);
      }
    );
    return {
      text,
      obj,
    };
  },
};
</script>