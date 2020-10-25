<template>
  <div class="pt-8 max-w-screen-md mx-auto">
    <h1 class="text-5xl text-center">Your Remaining Life</h1>

    <div class="mt-6 w-24 max-w-full mx-auto">
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

    <div class="text-center mt-6">
      <p>Years: {{ remainingYears }} / {{ totalYears }}</p>
      <p>Months: {{ remainingMonths }} / {{ totalMonths }}</p>
      <p>Days: {{ remainingDays }} / {{ totalDays }}</p>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  data() {
    return {
      age: 30,
      death: 85,
    }
  },

  computed: {
    remainingYears(): number {
      return Math.max(0, this.death - this.age)
    },

    remainingMonths(): number {
      return this.remainingYears * 12
    },

    remainingDays(): number {
      return this.remainingYears * 365
    },

    totalYears(): number {
      return this.death
    },

    totalMonths(): number {
      return this.totalYears * 12
    },

    totalDays(): number {
      return this.totalYears * 365
    },
  },
})
</script>
