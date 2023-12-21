<template>
  <pre class="code-block">{{ JSON.stringify(list, null, 2) }}</pre>
</template>

<script setup>
defineProps({
  list: {
    type: Array,
    required: true
  }
});
</script>