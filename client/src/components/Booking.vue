<template lang="html">
  <div id='booking-vue'>
    <div id="booking-container">


    <h4>{{booking.name}}</h4>
    <p>{{booking.email}}</p>
    <p v-if="booking.checkedInStatus">Customer Checked In</p>
    <p v-if="!booking.checkedInStatus">Customer Not Checked In</p>
    
    <button type="button" name="update" v-on:click="updateBooking(booking._id)">
      Change Check In Status</button>
    <button type="button" name="delete" v-on:click="deleteBooking(booking._id)">
      Delete Booking</button>

    </div>
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
    
    updateBooking(id){
      const updatedBooking = {
        name: this.booking.name,
        email: this.booking.email,
        checkedInStatus: this.booking.checkedInStatus
      }
      
      if (updatedBooking.checkedInStatus){
        updatedBooking.checkedInStatus = false
      }
      else {updatedBooking.checkedInStatus = true}
      
      HotelService.updateBooking(id, updatedBooking)
      .then((res) => eventBus.$emit('refresh-bookings'))
    }
  }
}


</script>

<style lang="css" scoped>

#booking-vue{
  color: white;
}

#booking-container{

}

</style>
