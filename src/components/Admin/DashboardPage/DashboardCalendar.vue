<script lang="ts">
import FullCalendar from "@fullcalendar/vue3";
import dayGridPlugin from "@fullcalendar/daygrid";
import listPlugin from "@fullcalendar/list";
import interactionPlugin from "@fullcalendar/interaction";
import axios from "axios";

export default {
  components: {
    FullCalendar // make the <FullCalendar> tag available
  },
  data() {
    return {
      calendarOptions: {
        plugins: [dayGridPlugin, interactionPlugin, listPlugin],
        showNonCurrentDates: false,
        height: 650,
        width: "100%",
        initialView: "dayGridMonth",
        moreLinkClick: "popover",
        dayMaxEvents: 2,
        views: {
          dayGridMonth: { buttonText: "Grid" },
          listDay: { buttonText: "Days" },
          listWeek: { buttonText: "Weeks" },
          listMonth: { buttonText: "Months" }
        },
        headerToolbar: {
          left: "prev,today,next",
          right: "title"
        },
        events: []
      }
    };
  },
  methods: {
    handleDateClick: function (arg: any) {
      alert("date click! " + arg.dateStr);
    }
  },
  mounted() {
    axios.get("/events").then((response) => {
      this.calendarOptions.events = response.data.data;
    });
  }

};
</script>

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
<template>
   <div>
    <FullCalendar :options="calendarOptions" class="w-[98%]" />
  </div>
  <div class="w-full my-4">
    <RouterLink
      to="/admin/calendar"
      class="px-4 py-2 text-xs font-bold text-white border-2 border-solid rounded-lg bg-secondary hover:bg-gray-900 gitborder-white-500"
    >
      Open Calendar</RouterLink
    >
  </div>
</template>
