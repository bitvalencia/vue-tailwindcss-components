<template>
  <section
      v-if="open"
      :class="{background: 'fixed z-40 inset-0 overflow-hidden'}"
      aria-labelledby="slide-over-title"
      role="dialog"
      aria-modal="true"
  >
    <div :class="{background: 'absolute inset-0 overflow-hidden'}">
      <div v-if="open && background" class="absolute inset-0" aria-hidden="true" @click.prevent="close"></div>
      <div v-if="open" class="fixed z-50 inset-y-0 right-0 pl-10 max-w-full flex">

        <transition
            enter-active-class="transform transition ease-in-out duration-500 sm:duration-700"
            enter-class="translate-x-full"
            enter-to-class="translate-x-0"
            leave-active-class="transform transition ease-in-out duration-500 sm:duration-700"
            leave-class="translate-x-0"
            leave-to-class="translate-x-full"
        >
          <div class="w-screen max-w-2xl">
            <div class="h-full flex flex-col py-6 bg-gray-50 shadow-xl overflow-y-scroll">
              <div class="px-4 sm:px-6">
                <div class="flex items-start justify-between">
                  <h2 class="text-lg font-medium text-gray-900" id="slide-over-title">
                    <slot name="title"></slot>
                  </h2>
                  <div class="ml-3 h-7 flex items-center">
                    <button @click.prevent="close" class="bg-gray-50 rounded-md text-gray-400 hover:text-gray-500 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">
                      <svg class="h-6 w-6" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" aria-hidden="true">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
                      </svg>
                    </button>
                  </div>
                </div>
              </div>
              <div class="mt-6 relative flex-1 px-4 sm:px-6">
                <slot name="content"></slot>
              </div>
            </div>
          </div>
        </transition>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  props: {
    open: {
      required: true,
    },
    background: {
      required: false,
      default: true
    }
  },
  methods: {
    close() {
      this.$emit('close')
    }
  },
}
</script>
