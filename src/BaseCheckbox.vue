<template>
  <input type="checkbox" :value="value" v-model="proxyChecked" :class="[widthClass]"
         class="rounded border-gray-300 text-indigo-600 shadow-sm focus:border-indigo-300 focus:ring focus:ring-indigo-200 focus:ring-opacity-50">
</template>

<script>
export default {
  props: {
    checked: {
      type: [Array, Boolean],
      default: false,
    },
    width: {
      default: '4'
    },
    value: {
      default: null,
    },
  },
  computed: {
    widthClass() {
      return {
        '4': 'w-4 h-4',
        '6': 'w-6 h-6',
      }[this.width.toString()]
    },
    proxyChecked: {
      get() {
        return this.checked;
      },
      set(val) {
        this.$emit('input', val);
      },
    },
  },
}
</script>
