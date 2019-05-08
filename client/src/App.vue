<template>
  <div id="app">
  <booking-form/>
  <bookings-grid/>
  </div>
</template>

<script>
import BookingForm from '@/components/Booking.vue';
import BookingsGrid from '@/components/BookingsGrid.vue';

export default {
  name: 'app',
  components: {
    'booking-form': BookingForm,
    'bookings-grid': BookingsGrid
  }
}
</script>

<style>
#app {
}
</style>
