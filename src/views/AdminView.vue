<script lang="ts" setup>
import { onMounted, ref } from "vue";
import { initFlowbite } from "flowbite";
import axios from "axios";
import router from "../router"
import { RouterLink, RouterView } from "vue-router";
const user = JSON.parse(localStorage.getItem("user") || "{}");

const name = ref("");
const username = ref("");
const role = ref("");

axios
  .get(`/users/${user.id}?profile=true`)
  .then((res) => {
    name.value = res.data.profile.lastName + " " + res.data.profile.firstName;
    username.value = res.data.username;
    role.value = res.data.role;
    console.log(res);
  })
  .catch((error) => {
    console.log(error);
  });

// initialize components based on data attribute selectors
onMounted(() => {
  initFlowbite();
});

// Log Out
function logOut() {
  localStorage.removeItem("user");
  router.push("/");
}
</script>
<template>
  <aside id="sidebar"
    class="fixed top-0 left-0 z-40 w-64 h-screen transition-transform -translate-x-full border-gray-200 bg-violet sm:translate-x-0 dark:bg-gray-800 dark:border-gray-700"
    aria-label="Sidebar">
    <img src="/blinc-logo.png" alt="logo" class="w-40 pt-8 pb-16 mx-auto h-15" :draggable="false"/>
    <div class="block w-5/6 mx-auto bg-white border border-gray-200 rounded-lg shadow hover:bg-gray-100 dark:bg-gray-800 dark:border-gray-700 dark:hover:bg-gray-700">
    <p class="text-xl text-center text-black dark:text-white" role="none">{{ name }}</p>
    <hr class="w-2/3 mx-auto bg-gray-700 border-[1.5] dark:bg-gray-700" />
    <p class="pb-2 text-xl font-medium text-center text-black truncate dark:text-gray-300" role="none">{{ role }}</p>
  </div>
  
    <div class="h-full px-3 py-4 overflow-y-auto bg-violet dark:bg-gray-800">
      <ul class="space-y-2 font-medium">
        <li>
          <hr class="w-5/6 mt-12 mb-8 mx-auto bg-gray-700 border-[1.5] dark:bg-gray-700" />
          </li>
        <li>
          <RouterLink to="/admin/dashboard"
            class="flex items-center p-2 text-white border-pink-300 text-s hover:bg-gradient-to-l from-grad hover:border-r-8">
            <img src="/dashboard.svg" class="pr-3" alt="">
            Dashboard
          </RouterLink>
        </li>
        <li>
          <RouterLink to="/admin/attendances"
            class="flex items-center p-2 text-white border-pink-300 text-s hover:bg-gradient-to-l from-grad hover:border-r-8">
            <img src="/attendance.svg" class="pr-3" alt="" />
            Attendance
        </RouterLink>
        </li>
        <li>
          <RouterLink to="/admin/employees"
            class="flex items-center p-2 text-white border-pink-300 text-s hover:bg-gradient-to-l from-grad hover:border-r-8">
            <img src="/employees.svg" class="pr-3" alt="" />
            Employees
          </RouterLink>
        </li>
        <li>
          <RouterLink to="/admin/requests"
            class="flex items-center p-2 text-white border-pink-300 text-s hover:bg-gradient-to-l from-grad hover:border-r-8">
            <img src="/requests.svg" class="pr-3" alt="" />
            Requests
          </RouterLink>
        </li>
        <li>
          <a href="/admin/calendar" class="flex items-center p-2 text-white border-pink-300 text-s hover:bg-gradient-to-l from-grad hover:border-r-8">
            <img src="/calendar.svg" class="pr-3" alt="" />
            Calendar
          </a>
        </li>
        <li>
          <RouterLink to="/admin/profile" class="flex items-center p-2 text-white border-pink-300 text-s hover:bg-gradient-to-l from-grad hover:border-r-8">
            <img src="/profile.svg" class="pr-3" alt="">
            Profile
          </RouterLink>
        </li>
      </ul>
      <ul class="fixed space-y-2 font-medium bottom-16">

<li>
  <a @click="logOut()" href="#" class="flex items-center p-2 text-white border-pink-300 text-s dark:text-white hover:bg-gradient-to-l from-grad hover:border-r-8">
    <span class="ml-3 whitespace-nowrap">Logout</span>
    <img src="/logout.svg" class="ml-2" alt="">
  </a>
</li>
</ul>
</div>
</aside>

<div class="bg-primary">
  <div class="bg-white sm:ml-64 rounded-l-[2.5rem] min-h-screen ">
    <div class="p-1">
      
       
     
    </div>

    <div class="p-4">
      <div class="p-4 bg-slate-200 rounded-xl">
        <RouterView />
      </div>
    </div>
  </div>
</div>
</template>
