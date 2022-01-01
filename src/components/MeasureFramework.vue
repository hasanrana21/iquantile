<template>
  <section>
    <h3 class="text-2xl font-semibold mt-10 mb-3">
      Outcome Measurement Framework
    </h3>

    <div class="p-6 bg-white rounded-lg">
      h
      <!-- Programs Problem -->
      <h3 class="text-2xl font-bold text-indigo-700">Inputs</h3>
      <div class="">
        <label for="problem"
          >What issues are you trying to solve in this program?</label
        >
        <br />
        <input
          type="text"
          id="problem"
          placeholder="Write problems and press enter"
        />

        <!-- Show Tags -->
        <div class="flex">
          <p class="bg-gray-300 px-3 py-2 rounded-lg m-2">
            problem

            <span class="mx-2 font-bold cursor-pointer">X</span>
          </p>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
label {
  @apply text-lg;
}
input {
  @apply text-lg px-2 py-2 w-full mt-1 mb-3 border-2 border-gray-400 rounded;
}
</style>
