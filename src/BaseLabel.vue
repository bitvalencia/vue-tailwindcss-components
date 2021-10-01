<template>
  <label class="block font-medium text-sm text-gray-700">
    <span v-if="value">{{ value }}</span>
    <span v-else><slot></slot></span>
    <span v-if="mandatory" class="text-red-600">*</span>
  </label>
</template>

<script>
export default {
  props: {
    mandatory: {
      type: Boolean,
      default: false,
    },
    value: {
      required: false
    },
  }
}
</script>
