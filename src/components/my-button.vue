<template>
  <button
    :disabled="disabled"
    class="my-button"
    :class="[
      colorComputed,
      sizeComputed
    ]"
  >
    <slot></slot>
  </button>
</template>

<script setup>
import { computed } from "vue";

const props = defineProps({
  color: {
    type: String,
    default: '',
    validator: (color) => /red|green|blue/.test(color),
  },
  size: {
    type: String,
    default: 'md',
    validator: (soze) => /sm|md|lg/.test(soze),
  },
  disabled: {
    type: Boolean,
    default: false,
  }
});

const colorComputed = computed(() => props.color ? `my-button-color-${props.color}` : '');
const sizeComputed = computed(() => props.size ? `my-button-size-${props.size}` : '');
</script>

<style lang="scss" scoped>
.my-button {
  align-items: center;
  color: white;
  cursor: pointer;
  display: flex;
  font-family: Open Sans,sans-serif;
  font-weight: 600;
  justify-content: center;
  outline: none !important;
  transition: all .3s linear;

  &-color {
    &-red {
      background-color: red;
      border: 2px solid red;
    }
    &-green {
      background-color: green;
      border: 2px solid green;
    }
    &-yellow {
      background-color: yellow;
      border: 2px solid yellow;
    }
  }

  &-size {
    &-sm {
      border-radius:8px;
      -moz-column-gap:8px;
      column-gap:8px;
      font-size:16px;
      height:32px;
      padding:8px 12px
    }
    &-md {
      border-radius:16px;
      -moz-column-gap:8px;
      column-gap:8px;
      font-size:16px;
      height:48px;
      padding:16px 24px
    }
    &-lg {
      border-radius:16px;
      -moz-column-gap:12px;
      column-gap:12px;
      font-size:20px;
      height:56px;
      padding:16px 24px
    }
  }
}
</style>
