<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <div>{{ text }}</div>
  <div>{{ obj.counter }}</div>
  <div>FullName: {{ fullName }}</div>
</template>

<script>
import { toRefs, ref, computed, reactive, watch } from "vue";

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

    expose({
      fullName,
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