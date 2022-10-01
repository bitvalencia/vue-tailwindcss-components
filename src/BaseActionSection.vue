<template>
  <div class="md:grid md:grid-cols-3 md:gap-6">
    <base-section-title>
      <template #title>
        <slot name="title"></slot>
      </template>
      <template #description>
        <slot name="description"></slot>
      </template>
    </base-section-title>

    <div class="mt-5 md:mt-0 md:col-span-2">
      <div class="px-4 py-5 sm:p-6 bg-white shadow sm:rounded-lg">
        <slot name="content"></slot>
      </div>
    </div>
  </div>
</template>

<script>
import BaseSectionTitle from './BaseSectionTitle.vue'

export default {
  components: {
    BaseSectionTitle,
  }
}
</script>
