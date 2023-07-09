<script lang="ts" setup>
import CalendarView from "./CalendarPage/CalendarView.vue";
</script>
<template>

  <div class="w-full ">
    <div class="p-2  py-16 rounded-lg w-3/4 mx-auto shadow-md bg-white">
   <CalendarView class="w-[80%] mx-auto bg-white" />
  </div></div>
</template>
<style>
<style>

.fc-day{
background:#fff;
color: #374151;
font-weight: 700;
}
.fc-daygrid{
background:#fff;
color: #374151;
font-weight: 500;
}

.fc-col-header-cell{
background:#fff;
color: #374151;
}
h2{
  color: #374151;
  font-weight: 800;
}
</style>