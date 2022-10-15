<template>
  <div :class="['h-screen w-screen', 'flex', 'items-center justify-center']">
    <Calendar />
  </div>
</template>

<script>
import Calendar from "./components/Calendar.vue";
export default {
  data() {
    return {};
  },
  components: {
    Calendar,
  },
};
</script>
