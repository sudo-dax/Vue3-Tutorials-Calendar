<template>
  <div class="m-auto">
    <h2 class="text-2xl my-2 text-center">{{ currentYear }} Almanac</h2>

    <h3> {{daysInMonth()}} days in this month</h3>
    <h3> {{startDay()}} is 1st day this month</h3>
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
        v-for="num in daysInMonth(currentYear,currentMonth)"
        :key="num"
      >
        {{ num }}
      </p>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentMonth: new Date().getMonth() + 1,
      currentMonthName: new Date().toLocaleString("default", {month: "long",}),
      currentYear: new Date().getFullYear(),
      days: ["Sun", "Mon", "Tues", "Wed", "Thu", "Fri", "Sat"],
    };
  },

  methods: {
    daysInMonth() {
        const month = new Date().getMonth()+1
      return new Date(2022,month, 0).getDate();
    },
    startDay() {
        return new Date(this.currentYear,this.currentMonth).getDay()
    }
  },
};
</script>

<style></style>
