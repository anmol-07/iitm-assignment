<template>
  <div class="col-4 card">
    <div class="course-details-outer">
      <div class="course-heading">
        <div class="course-main-details-outer">
          <h4 class="course-name">{{courseDetails.courseTitle}}</h4>
          <div class="course-instructor-name">{{courseDetails.facultyName}}</div>
        </div>
      </div>

      <div class="course-detail-div">
        <span class="course-info-icon">
          <i class="fa-solid fa-circle-info"></i>
        </span>
        <span class="course-details-text"
          >Lorem Ipsum is simply dummy text of the printing and typesetting
          industry. Lorem Ipsum has been the industry's standard dummy text ever
          since the 1500s, when an unknown printer took a galley of type and
          scrambled it to make a type specimen book.</span
        >
      </div>
      <div class="course-detail-div">
        <span class="course-calendar-icon">
          <i class="fa-solid fa-calendar"></i>
        </span>
        <span class="course-details-text">
          <p class="course-type">{{courseDetails.courseType}}</p>
          <p class="course-start-end-date">
            <span>{{getReadableDate(courseDetails.start_date)}}</span> -
            <span>{{getReadableDate(courseDetails.end_date)}}</span>
          </p>
        </span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "CourseCard",
  props: {
    courseDetails: Object,
  },
  methods: {
    //function to get the user joined since date in human readable format
    getReadableDate(dateTimeStamp) {
      let theDate = new Date(dateTimeStamp * 1000);
      return theDate.toDateString();
    }
  },
};
</script>
