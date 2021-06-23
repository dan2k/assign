<template>
  <ul class="list-group mx-2">
    <li
      class="list-group-item text-left"
      v-for="(u, i) of users"
      :key="Number(i)"
    >
      <div class="row">
        <div class="col-sm-12 col-md-2">
          <i class="fa fa-user-o" aria-hidden="true"></i>
          &nbsp;
          {{ u.name }}
        </div>
        <div class="col-sm-12 col-md-10 mx-0">
          <i
            class="fa fa-tasks px-1"
            aria-hidden="true"
            v-for="(j, x) of assign
              .filter((it, i3) => it.users.toString().includes(u.user_id))
              .map((it, i3) => jobs.find((ob) => ob.job_id == it.job_id))"
            :key="x"
            :style="{ color: j.color }"
          ></i> 
        </div>
      </div>
    </li>
  </ul>
</template>

<script setup>
import { ref } from "vue";
const users = ref([
  { user_id: 0, name: "แสงทอง หวลไข่" },
  { user_id: 1, name: "นันทภัค ไพรศรี" },
  { user_id: 2, name: "รัตภูมิ พิษเพ็ง" },
  { user_id: 3, name: "ทดสอบ ทดสอบ" },
]);
const jobs = ref([
  { job_id: 0, title: "่job1", color: "red" },
  { job_id: 1, title: "่job2", color: "blue" },
  { job_id: 2, title: "่job3", color: "green" },
  { job_id: 3, title: "่job4", color: "black" },
]);
const assign = ref([
  { as_id: 0, job_id: 0, users: [0, 1, 2] },
  { as_id: 1, job_id: 1, users: [0, 1] },
  { as_id: 2, job_id: 2, users: [0, 1] },
  { as_id: 3, job_id: 3, users: [0, 3] },
  { as_id: 4, job_id: 0, users: [0, 1, 2] },
]);
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.list-group-item {
  text-align: left;
}
</style>