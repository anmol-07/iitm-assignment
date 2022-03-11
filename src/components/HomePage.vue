<template>
  <div class="container custom-outer-container">
    <div class="row">
      <div class="col-3">
        <side-bar-filter
          @changeInput="filterResultsByInput"
          @changeOptions="filterResultsByOptions"
        ></side-bar-filter>
      </div>
      <div class="col-9">
        <h6>5 courses open for registration</h6>
        <div class="course-cards-outer">
          <course-card
            v-for="course in getFilteredList"
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
      filteredList: [],
      currentSelectedCategory: "",
      currentInputValue: "",
    };
  },
  methods: {
    filterResultsByInput(inputValue) {
      this.currentInputValue = inputValue;
      this.filteredList = this.courseList.filter((course) => {
        return (
          course.courseTitle.toLowerCase().includes(inputValue.toLowerCase()) ||
          course.facultyName.toLowerCase().includes(inputValue.toLowerCase()) ||
          course.courseCategory.filter((x) =>
            x.toLowerCase().includes(inputValue.toLowerCase())
          ).length > 0
        );
      });
      console.log(this.currentSelectedCategory);
      if (this.currentSelectedCategory) {
        this.filteredList = this.filteredList.filter(
          (course) =>
            course.courseCategory.filter(
              (x) =>
                x.toLowerCase() === this.currentSelectedCategory.toLowerCase()
            ).length > 0
        );
      }
    },
    filterResultsByOptions(selectedCategory) {
      this.currentSelectedCategory = selectedCategory;
      console.log(selectedCategory);
      this.filteredList = this.courseList.filter((course) => {
        return (
          course.courseTitle
            .toLowerCase()
            .includes(this.currentInputValue.toLowerCase()) ||
          course.facultyName
            .toLowerCase()
            .includes(this.currentInputValue.toLowerCase()) ||
          course.courseCategory.filter(
            (x) => x.toLowerCase() === selectedCategory.toLowerCase()
          ).length > 0
        );
      });
    },
  },

  computed: {
    getFilteredList() {
      return this.filteredList.length > 0 ? this.filteredList : this.courseList;
    },
  },
};
</script>
