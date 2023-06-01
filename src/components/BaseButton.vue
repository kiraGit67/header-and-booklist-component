<template>
  <button :class="styling" v-on:click="$emit('button-clicked')">
    <slot />
  </button>
</template>

<script>
export default {
  emits: ["button-clicked"],
  props: {
    /*
    text: {
      type: String,
      required: true,
    },
    */
    variant: {
      type: String,
      default: "primary",
      validator(propValue) {
        return ["primary", "secondary"].includes(propValue);
      },
    },
  },
  computed: {
    styling() {
      return ["btn", `btn--${this.variant}`];
    },
  },
  /*
  methods: {
    emit() {
      this.$emit("button-clicked");
    },
  },
  */
};
</script>

<style scoped>
.btn {
  border: 3px solid transparent;
  border-radius: 3px;
  padding: 5px;
  cursor: pointer;
}

.btn--primary {
  border-color: var(--primary);
  background-color: transparent;
  color: var(--primary);
}

.btn--primary:hover {
  border-color: var(--primary-dark);
  background-color: var(--primary);
  color: white;
}

.btn--secondary {
  border-color: var(--secondary);
  background-color: transparent;
  color: var(--secondary);
}

.btn--secondary:hover {
  background-color: var(--secondary);
  color: #000;
}
</style>
