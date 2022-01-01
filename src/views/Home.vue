<template>
  <div class="px-24 py-12 bg-gray-200">
    <ProgramDesign />
    <MeasureFramework />
  </div>
</template>

<script>
// @ is an alias to /src
import ProgramDesign from "@/components/ProgramDesign";
import MeasureFramework from "../components/MeasureFramework.vue";

export default {
  name: "Home",
  components: {
    ProgramDesign,
    MeasureFramework,
  },
};
</script>
