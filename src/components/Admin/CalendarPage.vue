<script lang="ts" setup>
import CalendarView from "./CalendarPage/CalendarView.vue";
import CalendarEventControls from "./CalendarPage/CalendarEventControls.vue";
</script>
<template>
  <div class="grid grid-cols-6 gap-10">
    
    <CalendarView class="w-[98%] col-span-6 rounded-lg p-2 bg-white lg:col-span-4" />
    <CalendarEventControls />
  </div>

</template>
