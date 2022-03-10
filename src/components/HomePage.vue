<template>
  <div class="container custom-outer-container">
    <div class="row">
      <div class="col-3">
          <side-bar-filter @changeInput="filterResultsByInput"></side-bar-filter>
      </div>
      <div class="col-9">
        <h6>5 courses open for registration</h6>
        <div class="course-cards-outer">
        <course-card
          v-for="course in courseList"
          :key="course.id"
          :courseDetails="course"
        ></course-card>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import CourseCard from "./CourseCard.vue";
import SideBarFilter from "./SideBarFilter.vue";
import config from "./../sampleApi.json";

export default {
  name: "HomePage",
  components: { CourseCard, SideBarFilter },
  mounted() {
    this.courseList = config;
  },
  data() {
    return {
      courseList: [],
      filteredList: []
    };
  },
  methods : {
    filterResultsByInput(inputValue) {
      console.log(inputValue);
    }
  }
};
</script>
