<template>
  <div>
    <ul v-for="technology in technologies" v-bind:key="technology.name" class="technologies">
      <li>
        <b>{{technology.name}}</b>: {{technology.details}}
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'Tech',
  data() {
    return {
      technologies: []
    };
  },
  mounted() {
    axios
      .get(`${process.env.VUE_APP_API_URL}/api/technologies`)
      .then(response => (this.technologies = response.data));
  }
};
</script>

<style scoped>
.technologies {
  margin-top: 5px;
}
</style>
