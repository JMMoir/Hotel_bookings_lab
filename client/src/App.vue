<template>
  <div id="app">
    <Header text="The CodeClan Inn"/>
  <booking-form/>
  <bookings-grid/>
  </div>
</template>

<script>
import BookingForm from '@/components/BookingForm.vue';
import BookingsGrid from '@/components/BookingsGrid.vue';
import Header from '@/components/Header.vue';

export default {
  name: 'app',
  components: {
    'booking-form': BookingForm,
    'bookings-grid': BookingsGrid,
    'Header': Header
  }
}
</script>

<style>
#app {
  background:url(https://hauteliving.com/wp-content/uploads/2017/04/chicago-athletic-association-hotel.jpg) no-repeat;
  height: 100%;
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
}
</style>
