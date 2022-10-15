<template>
    <div :class="[
    'w-screen h-screen',
    'flex flex-col',
    'justify-center items-center',
    'gap-5',
  ]">
    <input type="range" v-model="val" :min="min" :max="max" />
    <ProgressBar
      :currentVal="val" :minVal="min" :maxVal="max"
      v-slot="{ percent }"
    >
      已下載 {{ percent }} %
    </ProgressBar>

    </div>
</template>

<script>
import ProgressBar from './components/ProgressBar.vue'
export default {
  components: {
    ProgressBar,
  },
  data() {
    return {
      min: 0,
      max: 100,
      val: 100,
    }
  },
}
</script>