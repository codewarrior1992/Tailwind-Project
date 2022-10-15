<template>
  <div
    :class="[
      'fixed top-0 left-0',
      'h-screen w-screen',
      'p-5',
      'flex items-center justify-center',
      showed ? 'opacity-100' : 'pointer-events-none opacity-0',
      'transition-all duration-300',
    ]"
  >
    <!-- Modal-Overlay -->
    <div
      class="absolute top-0 left-0 h-full w-full bg-black/50"
      @click="closing()"
    />

    <!-- Modal-Window -->
    <div
      :class="[
        'z-10 w-full max-w-sm overflow-hidden rounded-md bg-white',
        showed ? 'scale-100' : 'scale-0',
        'transition-all duration-300',
      ]"
    >
      <div class="flex items-center justify-between border-b-2 p-3">
        <div class="font-bold text-gray-700">
          {{ title }}
        </div>
        <div
          class="h-7 w-7 cursor-pointer rounded-md p-1 transition-all hover:bg-gray-200 active:scale-90"
          @click="closing()"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="h-full w-full"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M6 18L18 6M6 6l12 12"
            />
          </svg>
        </div>
      </div>

      <div>
        <slot name="itemContent">
          <div class="p-3">
            <slot name="itemText"> 這是 Modal 視窗 </slot>
          </div>
        </slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Modal",
  props: {
    showModal: {},
    title: {
      default: "注意",
    },
  },
  data() {
    return {
      showed: true,
    };
  },
  mounted() {
    this.showed = this.showModal;
  },
  watch: {
    showModal(newVal, oldVal) {
      this.showed = newVal;
    },
  },
  methods: {
    closing() {
      this.showed = false;
      this.$emit("closing");
    },
  },
};
</script>
