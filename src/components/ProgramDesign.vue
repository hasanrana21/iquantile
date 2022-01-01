<template>
  <section>
    <h3 class="text-3xl font-semibold my-3">Program Design</h3>

    <div class="p-6 bg-white rounded-lg">
      <!-- Program -->
      <div class="grid grid-cols-12 space-x-8">
        <div class="col-span-6">
          <label for="program">What’s the title of your program?</label> <br />
          <input
            type="text"
            id="program"
            placeholder="Please enter the title of your program"
          />
        </div>
        <div class="col-span-3">
          <label for="start-date">Start Date</label> <br />
          <input type="text" id="start-date" placeholder="E.g. 01/01/2020" />
        </div>
        <div class="col-span-3">
          <label for="end-date">End Date</label> <br />
          <input type="text" id="end-date" placeholder="end-date" />
        </div>
      </div>

      <!-- Programs Problem -->
      <div class="py-4">
        <label for="problem"
          >What issues are you trying to solve in this program?</label
        >
        <br />
        <input
          type="text"
          id="problem"
          v-model="programsProblem"
          placeholder="Write problems and press enter"
          @keyup.enter="problemsTag"
        />

        <!-- Show Tags -->
        <div class="flex">
          <p
            v-for="(problem, index) in problems"
            :key="index"
            class="bg-gray-300 px-3 py-2 rounded-lg m-2"
          >
            {{ problem }}

            <span
              class="mx-2 font-bold cursor-pointer"
              @click="deleteProblemsTag(index)"
              >X</span
            >
          </p>
        </div>
      </div>

      <!-- Programs Goals -->
      <div class="py-4">
        <label for="program-goals"
          >What are your goals for this program?
        </label>
        <br />
        <input
          type="text"
          id="program-goals"
          v-model="goalsProgram"
          placeholder="Write goals and press enter"
          @keyup.enter="goalsTag"
        />

        <!-- Show Tags -->
        <div class="flex">
          <p
            v-for="(goal, index) in goals"
            :key="index"
            class="bg-gray-300 px-3 py-2 rounded-lg m-2"
          >
            {{ goal }}

            <span
              class="mx-2 font-bold cursor-pointer"
              @click="deleteGoalsTag(index)"
              >X</span
            >
          </p>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      goalsProgram: "",
      goals: [],
      programsProblem: "",
      problems: [],
    };
  },
  mounted() {
    console.log(this.goalsTag);
  },
  methods: {
    goalsTag() {
      if (!this.goalsProgram == "") {
        this.goals.push(this.goalsProgram);
      }
    },
    problemsTag() {
      if (!this.programsProblem == "") {
        this.problems.push(this.programsProblem);
      }
    },
    deleteGoalsTag(id) {
      this.goals.splice(id, 1);
    },
    deleteProblemsTag(id) {
      this.problems.splice(id, 1);
    },
  },
};
</script>

<style scoped>
label {
  @apply text-lg;
}
input {
  @apply text-lg px-2 py-2 w-full mt-1 mb-3 border-2 border-gray-400 rounded;
}
</style>
