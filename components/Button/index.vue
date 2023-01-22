<template>
  <button
      :type="submit ? 'submit' : 'button'"
      :class="[
      styles.base,
      possibleStyles.includes(className) ? styles[className] : null,
    ]"
  >
    <slot></slot>
  </button>
</template>

<script setup lang="ts">
import * as styles from "./index.module.css"

const possibleStyles = ["reject", "warn", "secondary"]
defineProps({
  className: {
    type: String,
    default: null
  },
  submit: {
    type: Boolean,
    default: false
  }
})
</script>
