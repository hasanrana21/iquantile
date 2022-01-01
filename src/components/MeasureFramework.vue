<template>
  <section>
    <h3 class="text-2xl font-semibold mt-10 mb-3">
      Outcome Measurement Framework
    </h3>

    <div class="p-6 bg-white rounded-lg">
      <div class="mt-1 mb-5">
        <h3 class="text-2xl font-bold text-blue-700">Inputs</h3>
        <p class="font-semibold py-1">
          What resources are available for this program?
        </p>
      </div>

      <!-- Personal Input -->
      <div>
        <div class="flex my-3">
          <input
            type="checkbox"
            @click="checkPersonal = !checkPersonal"
            id="personal"
            class="w-7 h-7 mr-2"
          />
          <label for="personal">Personal</label>
        </div>

        <div v-if="checkPersonal">
          <h4 class="font-semibold py-1">
            Which personnel will be in this program?
          </h4>
          <select
            name="personal"
            id="personal"
            v-model="optionPersonal"
            @change="personalTags"
          >
            <option selected disabled>Select personnel ---</option>
            <option>Santa Shields</option>
            <option>Lester Hudson</option>
            <option>Personal 3</option>
            <option>Personal 4</option>
          </select>

          <!-- Show Tags -->
          <div class="flex">
            <p
              v-for="(tag, index) in personalSelections"
              :key="index"
              class="bg-gray-300 px-3 py-2 rounded-lg m-2"
            >
              {{ tag }}
              <span
                class="mx-2 font-bold cursor-pointer"
                @click="deletePersonalTag(index)"
                >X</span
              >
            </p>
          </div>
        </div>
      </div>

      <!-- Funding Input -->
      <div>
        <div class="flex my-3">
          <input
            type="checkbox"
            @click="checkFunding = !checkFunding"
            id="funding"
            class="w-7 h-7 mr-2"
          />
          <label for="funding">Funding</label>
        </div>

        <div v-if="checkFunding">
          <h4 class="font-semibold py-1">Add funding source</h4>
          <select
            name="funding"
            id="funding"
            v-model="funding"
            @change="fundingTags"
          >
            <option selected disabled>Select and press enter ---</option>
            <option>Government Fund</option>
            <option>Private Fund</option>
            <option>Funding 3</option>
            <option>Funding 4</option>
          </select>

          <!-- Show Tags -->
          <div class="flex">
            <p
              v-for="(tag, index) in fundingSelections"
              :key="index"
              class="bg-gray-300 px-3 py-2 rounded-lg m-2"
            >
              {{ tag }}
              <span
                class="mx-2 font-bold cursor-pointer"
                @click="deleteFunding(index)"
                >X</span
              >
            </p>
          </div>
        </div>
      </div>

      <!-- Partnership Input -->
      <div>
        <div class="flex my-3">
          <input
            type="checkbox"
            @click="checkPartnership = !checkPartnership"
            id="partnership"
            class="w-7 h-7 mr-2"
          />
          <label for="partnership">Partnership</label>
        </div>

        <div v-if="checkPartnership">
          <h4 class="font-semibold py-1">
            Who are also partnering with you in this program?
          </h4>
          <select
            name="partnership"
            id="partnership"
            v-model="partnership"
            @change="partnershipTags"
          >
            <option selected disabled>Select partner organizations ---</option>
            <option>Collier and Sons</option>
            <option>Leuschke Grouppartnership</option>
            <option>partnership 3</option>
            <option>partnership 4</option>
          </select>

          <!-- Show Tags -->
          <div class="flex">
            <p
              v-for="(tag, index) in partnershipSelections"
              :key="index"
              class="bg-gray-300 px-3 py-2 rounded-lg m-2"
            >
              {{ tag }}
              <span
                class="mx-2 font-bold cursor-pointer"
                @click="deletePartnership(index)"
                >X</span
              >
            </p>
          </div>
        </div>
      </div>

      <!-- Others Input -->
      <div>
        <div class="flex my-3">
          <input
            type="checkbox"
            @click="checkOther = !checkOther"
            id="other"
            class="w-7 h-7 mr-2"
          />
          <label for="other">Other</label>
        </div>

        <div v-if="checkOther">
          <h4 class="font-semibold py-1">What other resources you have?</h4>
          <input
            type="text"
            name="partnership"
            id="partnership"
            v-model="other"
            @keyup.enter="otherTags"
            placeholder="Write and press enter"
          />

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
  data() {
    return {
      // Personal
      checkPersonal: false,
      optionPersonal: "",
      personalSelections: [],
      // Funding
      checkFunding: false,
      funding: "",
      fundingSelections: [],
      // Partnership
      checkPartnership: false,
      partnership: "",
      partnershipSelections: [],
      // Others
      checkOther: false,
      other: "",
      otherSelections: [],
    };
  },
  methods: {
    // Personal Input Functions
    personalTags() {
      if (!this.optionPersonal == "") {
        this.personalSelections.push(this.optionPersonal);
      }
    },
    deletePersonalTag(item) {
      this.personalSelections.splice(item, 1);
    },

    // Funding Input Functions
    fundingTags() {
      if (!this.funding == "") {
        this.fundingSelections.push(this.funding);
      }
    },
    deleteFunding(item) {
      this.fundingSelections.splice(item, 1);
    },

    // Partnership Input Functions
    partnershipTags() {
      if (!this.partnership == "") {
        this.partnershipSelections.push(this.partnership);
      }
    },
    deletePartnership(item) {
      this.partnershipSelections.splice(item, 1);
    },

    // Other Input Functions
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
input[type="text"],
select {
  @apply text-lg px-2 py-2 w-full mt-1 mb-3 border-2 border-gray-400 rounded;
}
</style>
