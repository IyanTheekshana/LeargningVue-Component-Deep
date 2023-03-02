<template>
  <div>
    <the-header></the-header>
    <!-- <badge-list></badge-list>
    <user-info
      :full-name="activeUser.name"
      :info-text="activeUser.description"
      :role="activeUser.role"
    ></user-info>
    <course-goal>
      <template #default="slotProps">
        <h2>{{ slotProps.item }}</h2>
        <p>...</p>
      </template>
    </course-goal> -->
    <button v-on:click="setSelectedComponent('active-goal')">
      Active Goal
    </button>
    <button v-on:click="setSelectedComponent('manage-goals')">
      Manage Goal
    </button>
    <!-- <active-goal v-if="selectedComponent === 'active-goal'"></active-goal>
    <manage-goals v-if="selectedComponent === 'manage-goals'"></manage-goals> -->
    <keep-alive>
      <component v-bind:is="selectedComponent"></component>
    </keep-alive>
  </div>
</template>

<script>
import TheHeader from "./components/TheHeader.vue";
// import BadgeList from "./components/BadgeList.vue";
// import UserInfo from "./components/UserInfo.vue";
// import CourseGoals from "./components/CourseGoals.vue";
import ActiveGoals from "./components/ActiveGoals.vue";
import ManageGoals from "./components/ManageGoals.vue";

export default {
  components: {
    "the-header": TheHeader,
    // "badge-list": BadgeList,
    // "user-info": UserInfo,
    // "course-goal": CourseGoals,
    "active-goal": ActiveGoals,
    "manage-goals": ManageGoals,
  },
  data() {
    return {
      selectedComponent: "active-goal",
      activeUser: {
        name: "Maximilian Schwarzmüller",
        description: "Site owner and admin",
        role: "admin",
      },
    };
  },
  methods: {
    setSelectedComponent(cmp) {
      this.selectedComponent = cmp;
    },
  },
};
</script>

<style>
html {
  font-family: sans-serif;
}

body {
  margin: 0;
  /* background-color: rgb(119, 119, 119); */
}
</style>
