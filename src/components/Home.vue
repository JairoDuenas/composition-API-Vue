<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <div>{{ text }}</div>
  <div>{{ obj.counter }}</div>
  <div>FullName: {{ fullName }}</div>
  <div>{{ username }}</div>
  <button ref="btn">Click!</button>
</template>

<script>
import { toRefs, ref, computed, reactive, watch, inject } from "vue";

export default {
  props: {
    firstName: String,
    lastName: String,
  },

  setup(props, { expose }) {
    const text = ref("Hola Vue");
    const obj = reactive({ counter: 0 });

    setInterval(() => obj.counter++, 1000);

    const { firstName, lastName } = toRefs(props);

    const fullName = computed(() => {
      return `${firstName.value} ${lastName.value}`;
    });

    const username = inject("username");

    expose({
      fullName,
    });

    const btn = ref(null);
    console.log(btn.value);

    watch(btn, (valor) => {
      console.log(valor);
    });

    return {
      text,
      obj,
      fullName,
      username,
      btn,
    };
  },
};
</script>