<template>
  <div class="home">
    <ToDo />
  </div>
</template>

<script>
// @ is an alias to /src
import ToDo from "@/components/ToDo.vue";

export default {
  name: "HomeView",
  components: {
    ToDo,
  },
};
</script>
