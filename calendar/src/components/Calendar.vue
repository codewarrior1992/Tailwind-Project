<template>
  <div class="flex flex-col overflow-hidden rounded-md border">
    <div
      class="flex items-center justify-center border-b bg-blue-600 p-3 font-bold text-white"
    >
      {{ year }} {{ month }} 月
    </div>
    <div class="grid grid-cols-7 place-items-center">
      <div
        class="flex h-10 w-10 items-center justify-center text-xs font-bold"
        v-for="wd in weekDays"
        :key="wd"
      >
        {{ wd }}
      </div>
    </div>
    <div class="grid grid-cols-7 place-items-center">
      <div
        :class="[
          'h-10 w-10',
          'text-sm',
          'flex items-center justify-center',
          'text-gray-400',
          'rounded-full transition-all',
        ]"
        v-for="d in lastMonth"
        :key="d"
      >
        {{ d }}
      </div>
      <div
        :class="[
          'h-10 w-10',
          'text-sm',
          'flex items-center justify-center',
          year === today.getFullYear() &&
          month - 1 === today.getMonth() &&
          d === today.getDate()
            ? 'bg-blue-600 font-bold text-white'
            : 'hover:bg-gray-200',
          'rounded-full transition-all',
        ]"
        v-for="d in thisMonth"
        :key="d"
      >
        {{ d }}
      </div>

      <div
        :class="[
          'h-10 w-10',
          'text-sm',
          'flex items-center justify-center',
          'text-gray-400',
          'rounded-full transition-all',
        ]"
        v-for="d in nextMonth"
        :key="d"
      >
        {{ d }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SimpleCalendar",
  data() {
    return {
      weekDays: ["Su", "Mo", "Tu", "We", "Th", "Fr", "Sa"],
      year: 2021,
      month: 9,
      today: new Date(),
    };
  },
  mounted() {
    this.today = new Date();
    this.year = this.today.getFullYear();
    this.month = this.today.getMonth() + 1;
  },
  computed: {
    lastMonth() {
      const days = [];
      const current = new Date(this.year, this.month - 1, 1);
      const wd = current.getDay();
      for (let i = wd; i > 0; i--) {
        const temp = new Date(current);
        temp.setDate(current.getDate() - i);
        days.push(temp.getDate());
      }
      return days;
    },
    thisMonth() {
      const days = [];
      const current = new Date(this.year, this.month, 0);
      for (let i = 1; i <= current.getDate(); i++) {
        days.push(i);
      }
      return days;
    },
    nextMonth() {
      const count = 42 - this.lastMonth.length - this.thisMonth.length;
      const days = [];
      for (let i = 1; i <= count; i++) {
        days.push(i);
      }
      return days;
    },
  },
};
</script>
