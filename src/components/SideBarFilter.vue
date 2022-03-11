<template>
  <div class="filter-outer-container">
    <div class="search-box-container">
      <h6>Search For Keywords</h6>  
      <input @input="gettingInput" class="search-box" type="text" placeholder="Search..." name="courseSearch" />
    </div>
    <div class="course-category-outer">
      <h6>Category</h6>  
      <div>
        <label v-for="category in categoryOptions" :key="category.id">
          <input @change="gettingSlectedValue"
            type="radio"
            v-model="selectedCategory"
            :value="category.field"
            :name="category.label"
          />
          <span>{{ category.label }}</span>
        </label>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SideBarFilter",
  data() {
    return {
      selectedCategory: 'all',
      categoryOptions: [
        {
          id: 1,
          label: "All",
          field: "all",
        },
        {
          id: 2,
          label: "Computer",
          field: "computer",
        },
        {
          id: 3,
          label: "Engineering",
          field: "engineering",
        },
        {
          id: 4,
          label: "Mathematics",
          field: "mathematics",
        },
      ],
    };
  },
  methods : {
    gettingInput(event) {
      this.$emit('changeInput', event.target.value);
    },
    gettingSlectedValue() {
      this.$emit('changeOptions', this.selectedCategory);
    }
  }
};
</script>
