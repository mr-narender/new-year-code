<template>
  <div class="home">
    <News :year="year" :apiKey="apiKey" />
    <HappyNewYear :year="year" />
  </div>
</template>

<script>
// @ is an alias to /src
import HappyNewYear from "@/components/HappyNewYear.vue";
import News from "@/components/YearInReview.vue";

export default {
  data() {
    return {
      year: new Date().getFullYear(),
      apiKey: process.env.VUE_APP_API_KEYS,
    };
  },
  name: "Home",
  components: {
    HappyNewYear,
    News,
  },
};
</script>
