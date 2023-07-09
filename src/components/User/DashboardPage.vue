<script lang="ts" setup>
// import AttendanceChart from "./DashboardPage/AttendanceChart.vue";
import AttendancesCard from "./DashboardPage/AttendancesCard.vue";
// import LineChart from "./DashboardPage/LineChart.vue";
import DashboardCalendar from "@/components/User/DashboardPage/DashboardCalendar.vue";
import AttendanceTime from "@/components/User/DashboardPage/AttendanceTime.vue";
// import AdminHeader from "./DashboardPage/AdminHeader.vue";
</script>
<template>
  <div class="grid gap-4 lg:grid-cols-4 md:grid-cols-1">
    <div class="row-span-4 lg:col-span-3 md:col-span-1">
      <AttendancesCard />
    </div>
    <div class="lg:col-span-1 md:col-span-1">
      <AttendanceTime />
    </div>
    <div class="row-span-2 bg-white rounded-lg p-1 lg:col-span-1 md:col-span-1">
      <DashboardCalendar />
    </div>
  
  </div>
</template>
