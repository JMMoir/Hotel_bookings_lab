<template lang="html">
  <div>
    <form class="" action="index.html" method="post" v-on:submit="handleSubmit">

      <label for="name">Name: </label>
      <input type="text" name="name" v-model="name">

      <label for="email">Email: </label>
      <input type="text" name="email" v-model="email">

      <label for="checked_in_status">Checked In?</label>
      <input type="checkbox" name="checked_in_status" value="true" v-model="checkedInStatus">

      <input type="submit" name="submit" value="Enter Booking">

    </form>
  </div>
</template>

<script>
import { eventBus } from '@/main.js';
import HotelService from '@/services/HotelService.js';

export default {
  name: 'booking-form',
  data(){
    return {
      name: "",
      email: "",
      checkedInStatus: false
    }
  },
  methods: {
    handleSubmit(event){
      event.preventDefault()

      const booking = {
        name: this.name,
        email: this.email,
        checkedInStatus: this.checkedInStatus
      }

      HotelService.createBooking(booking)
      .then(res => eventBus.$emit('refresh-bookings', res))
    }
  }
}
</script>

<style lang="css" scoped>
</style>
