<template lang="html">
  <div>
    
    <h4>{{booking.name}}</h4>
    <p>{{booking.email}}</p>
    <p v-if="booking.checkedInStatus">Customer Checked In</p>
    <p v-if="!booking.checkedInStatus">Customer Not Checked In</p>
    
    <button type="button" name="update" v-on:click="updateBooking(booking)">
      Change Check In Status</button>
    <button type="button" name="delete" v-on:click="deleteBooking(booking._id)">
      Delete Booking</button>
      
  </div>
</template>

<script>
import { eventBus } from '@/main.js';
import HotelService from '@/services/HotelService.js';

export default {
  name: 'bookingItem',

  props: ['booking'],

  methods: {
    
    deleteBooking(id){
      HotelService.deleteBooking(id)
      .then((res) => eventBus.$emit('refresh-bookings'))
    },
    
    updateBooking(booking){
      if (booking.checkedInStatus){
        booking.checkedInStatus = false
      }
      else {booking.checkedInStatus = true}
      
      HotelService.updateBooking(booking)
      .then((res) => eventBus.$emit('refresh-bookings'))
    }
  }

}
</script>

<style lang="css" scoped>
</style>
