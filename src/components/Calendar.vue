<template>
  <div class="m-auto">
    <h2 class="text-2xl my-2 text-center">{{ currentYear }} Almanac</h2>

    <!-- <h3> {{daysInMonth()}} days in this month</h3> -->
    <!-- <h3> {{startDay()}} is 1st day this month</h3> -->
    <section class="mx-4 flex justify-between">
      <h3 class="font-bold">{{ currentMonthName }}</h3>
      <h3 class="font-bold">{{ currentYear }}</h3>
    </section>
    <section class="flex my-2">
      <p
        class="text-center"
        style="width: 14.285%"
        v-for="day in days"
        :key="day"
      >
        {{ day }}
      </p>
    </section>
    <section class="flex flex-wrap">
      <p
        class="text-center"
        style="width: 14.285%"
        v-for="num in startDay()"
        :key="num"
      ></p>
      <p
        class="text-center"
        style="width: 14.285%"
        v-for="num in daysInMonth()"
        :key="num"
        :class="currentDateClass(num)"
      >
        {{ num }}
      </p>
    </section>
    <section class="flex justify-between my-4">
      <button class="p-2 border rounded" @click="prev">Prev</button>
      <button class="p-2 border rounded" @click="next">Next</button>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
        currentDate: new Date().getDate(),
      currentMonth: new Date().getMonth(),
      currentYear: new Date().getFullYear(),
      days: ["Sun", "Mon", "Tues", "Wed", "Thu", "Fri", "Sat"],
    };
  },

  methods: {
    daysInMonth() {
      return new Date(this.currentYear, this.currentMonth + 1, 0).getDate();
    },
    startDay() {
      return new Date(this.currentYear, this.currentMonth).getDay();
    },
    next() {
      if (this.currentMonth === 11) {
        this.currentMonth = 0;
        this.currentYear++;
      } else {
        this.currentMonth++;
      }
    },
    prev() {
        if (this.currentMonth === 0) {
            this.currentMonth = 11
            this.currentYear--
        } else {
            this.currentMonth--;
        }
    },
    currentDateClass(num) {
        // console.log(new Date(this.currentYear, this.currentMonth, num).toDateString())
        // console.log(new Date().toDateString())
        const calendarFullDate = new Date(this.currentYear, this.currentMonth, num).toDateString()
        const currentFullDate = new Date().toDateString()
        return calendarFullDate === currentFullDate ? 'text-red-700' : ""
    }
  },

  computed: {
    currentMonthName() {
      return new Date(this.currentYear, this.currentMonth).toLocaleString(
        "default",
        { month: "long" }
      );
    },
  },
};
</script>

<style></style>
