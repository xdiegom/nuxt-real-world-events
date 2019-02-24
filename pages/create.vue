<template>
  <div class="flex justify-center">
    <div class="w-full md:w-4/5 rounded shadow-lg p-6">
      <div class="flex flex-col">
        <h1 class="font-black text-2xl sm:text-5xl">
          Create an Event
        </h1>
        <div class="mt-4">
          <form @submit.prevent="createEvent">
            <div class="flex flex-col">
              <span class="font-bold tracking-wide text-sm">Name</span>
              <input
                v-model="eventName"
                class="border border-green font-bold rounded p-4"
                type="text"
              >
            </div>

            <div class="flex flex-col md:flex-row justify-between mt-4">
              <div class="w-full md:w-1/2 md:mr-4">
                <span class="font-bold tracking-wide text-sm">From</span>
                <datetime
                  v-model="fromDate"
                  :format="{ year: 'numeric', month: 'long', day: 'numeric'}"
                  class="border border-green font-bold rounded p-4 theme-green"
                />
              </div>

              <div class="w-full md:w-1/2 mt-4 sm:mt-0">
                <span class="font-bold tracking-wide text-sm">To</span>
                <datetime
                  v-model="toDate"
                  :format="{ year: 'numeric', month: 'long', day: 'numeric'}"
                  class="border border-green font-bold rounded p-4 theme-green"
                />
              </div>
            </div>

            <div class="flex flex-col mt-4">
              <span class="font-bold tracking-wide text-sm">Short Description</span>
              <textarea
                v-model="eventDescription"
                maxlength="200"
                rows="4"
                class="border border-green font-bold rounded p-4"
                type="text"
              ></textarea>
            </div>

            <div class="flex justify-end mt-4">
              <button
                type="submit"
                class="border bg-green p-4 uppercase text-white font-bold tracking-wide rounded-lg"
              >
                Create Event
              </button>
            </div>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { Datetime } from 'vue-datetime'
import { formatDate } from '~/helpers/date'

export default {
  components: {
    Datetime
  },
  data() {
    return {
      eventName: null,
      eventDescription: null,
      fromDate: null,
      toDate: null
    }
  },
  computed: {
    minDate() {
      return formatDate(new Date())
    },
    maxDate() {
      const today = new Date()
      return formatDate(new Date(today.setDate(today.getDate() + (15 - 1))))
    }
  },
  methods: {
    createEvent() {
      /* eslint-disable */
      console.log(
        this.eventName,
        this.eventDescription,
        this.fromDate,
        this.toDate
      )
      this.$router.push({ name: 'index' })
    }
  }
}
</script>

<style>
textarea {
  resize: none;
}

.theme-green .vdatetime-popup__header,
.theme-green .vdatetime-calendar__month__day--selected > span > span,
.theme-green .vdatetime-calendar__month__day--selected:hover > span > span {
  @apply bg-green;
}

.theme-green .vdatetime-year-picker__item--selected,
.theme-green .vdatetime-time-picker__item--selected,
.theme-green .vdatetime-popup__actions__button {
  @apply text-green;
}
</style>
