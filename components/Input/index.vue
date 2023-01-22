<template>
  <input
      :type="type"
      :class="[styles.base]"
      :placeholder="placeholder"
  />
</template>

<script setup lang="ts">
import * as styles from "./index.module.css"

defineProps({
  type: {
    type: String,
    default: null
  },
  placeholder: {
    type: String,
    default: null
  },
})
</script>
