<template>
  <div class="pt-8 px-2 max-w-screen-md mx-auto">
    <h1 class="text-5xl text-center">Your Remaining Life</h1>

    <div class="flex justify-center mt-6">
      <div class="flex-initial px-4 py-2 m-2">
        <div class="w-24">
          <label
            class="text-center block text-gray-700 text-sm font-bold mb-2"
            for="age"
            >Your age</label
          >
          <input
            id="age"
            v-model="age"
            class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
            placeholder="30"
            type="number"
          />
        </div>
      </div>

      <div class="flex-initial px-4 py-2 m-2">
        <div class="w-24">
          <label
            class="text-center block text-gray-700 text-sm font-bold mb-2"
            for="death"
            >Death</label
          >
          <input
            id="death"
            v-model="death"
            class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
            placeholder="85"
            type="number"
          />
        </div>
      </div>
    </div>

    <div class="mt-6 shadow w-full bg-black">
      <div
        class="bg-green-500 text-xl leading-none py-3 text-center text-white"
        :style="`width: ${remainingPercentage}%`"
      >
        {{ remainingPercentage }}%
      </div>
    </div>

    <div class="text-center text-lg mt-6">
      <p>Remaining {{ remainingDays }} days.</p>
      <p>You lived {{ totalDays - remainingDays }} days.</p>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  data() {
    return {
      age: 23,
      death: 85,
    }
  },

  computed: {
    remainingYears(): number {
      return Math.max(0, this.death - this.age)
    },

    remainingDays(): number {
      return this.remainingYears * 365
    },

    totalYears(): number {
      return this.death
    },

    totalDays(): number {
      return this.totalYears * 365
    },

    remainingPercentage(): number {
      return Math.round((this.remainingYears / this.totalYears) * 100)
    },
  },
})
</script>
