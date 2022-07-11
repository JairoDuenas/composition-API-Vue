<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <div>{{ text }}</div>
  <div>{{ obj.counter }}</div>
  <div>FullName: {{ fullName }}</div>
</template>

<script>
import { ref, computed, reactive, watch } from "vue";

export default {
  setup() {
    const text = ref("Hola Vue");
    const obj = reactive({ counter: 0 });

    setInterval(() => obj.counter++, 1000);

    const firstName = ref("Jairo");
    const lastName = ref("Dueñas");

    const fullName = computed(() => {
      return `${firstName.value} ${lastName.value}`;
    });

    watch(
      () => obj.counter,
      (valor, anterior) => {
        console.log(valor, anterior);
      }
    );
    return {
      text,
      obj,
      fullName,
    };
  },
};
</script>