<template>
  <div>
    <select v-model="selectedOption" @change="onChange">
      <option v-for="option in options" :value="option.value" :key="option.value">
        {{ option.label }}
      </option>
    </select>
  </div>
</template>

<script>
const CategoryFile = '/data/category.json';

export default {
  data() {
    return {
      options: [],
      selectedOption: ''
    }
  },
  created() {
    fetch(CategoryFile)
      .then(response => response.json())
      .then(data => this.options = data);
  },
  methods: {
    onChange(e) {
      this.selectedOption = e.target.value
    }
  }
}
</script>
