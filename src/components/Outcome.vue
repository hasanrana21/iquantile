<template>
  <section class="bg-white rounded-lg p-6 my-6">
    <h3 class="text-2xl font-bold text-blue-700">OutCome</h3>
    <p class="font-semibold py-1">
      What are the intended outcomes of your program?
    </p>

    <!-- Dynamic Goals -->
    <div v-for="(goal, index) in goals" :key="index">
      <div class="my-6">
        <h4 class="text-red-600 text-lg font-semibold">Goal 01: {{ goal }}</h4>
        <p class="text-gray-400">Select measure parameters</p>
      </div>

      <!-- Goals Checkboxes -->
      <div>
        <div class="flex my-6">
          <input
            type="checkbox"
            @click="checkMeet = !checkMeet"
            id="meet"
            class="w-7 h-7 mr-2"
          />
          <label for="meet">Meet program goal</label>
        </div>
        <div class="flex my-6">
          <input
            type="checkbox"
            @click="checkNotMeet = !checkNotMeet"
            id="notMeet"
            class="w-7 h-7 mr-2"
          />
          <label for="notMeet">Did not meet program goal</label>
        </div>
        <!-- Other Checkbox -->
        <div>
          <div class="flex mt-6 mb-3 items-center">
            <div class="flex">
              <input
                type="checkbox"
                @click="checkOther = !checkOther"
                id="other"
                class="w-7 h-7"
              />
              <label for="other" class="mx-2">Other</label>
            </div>
            <input
              v-if="checkOther"
              type="text"
              v-model="other"
              @keyup.enter="otherTags"
              placeholder="Write"
            />
          </div>
          <!-- Show Tags -->
          <div class="flex">
            <p
              v-for="(tag, index) in otherSelections"
              :key="index"
              class="bg-gray-300 px-3 py-2 rounded-lg m-2"
            >
              {{ tag }}
              <span
                class="mx-2 font-bold cursor-pointer"
                @click="deleteOtherTags(index)"
                >X</span
              >
            </p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "Outcome",
  props: ["goals"],
  data() {
    return {
      checkMeet: false,
      checkNotMeet: false,
      checkOther: false,
      other: "",
      otherSelections: [],
      allGoals: [],
    };
  },
  beforeCreate() {},
  mounted() {
    if (localStorage.goals) {
      this.allGoals = JSON.parse(localStorage.getItem("goals")) || [];
    }
    console.log(this.goals);
  },
  methods: {
    //  Other Functions
    otherTags() {
      if (!this.other == "") {
        this.otherSelections.push(this.other);
      }
    },
    deleteOtherTags(item) {
      this.otherSelections.splice(item, 1);
    },
  },
};
</script>

<style scoped>
label {
  @apply text-lg;
}
input[type="text"] {
  @apply text-lg px-2 py-2 w-full border-2 border-gray-400 rounded;
}
</style>
