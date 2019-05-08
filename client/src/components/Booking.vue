<template lang="html">
  <div>
    <h4>{{booking.name}}</h4>
    <p>{{booking.email}}</p>
    <p v-if="booking.checkedInStatus">Customer Checked In</p>
    <button type="button" name="delete" v-on:click="deleteBooking">Delete Booking</button>
  </div>
</template>

<script>
import { eventBus } from '@/main.js';
import HotelService from '@/services/HotelService.js';

export default {
  name: 'booking',
  
  props: ['booking'],
  
  methods(){
    deleteBooking = function(id){
      HotelService.iNSERTFUNCTIONNAMEHERE!!(id)
      .then((res) => eventBus.$emit('refresh-bookings', res))
    }
  }
  
}
</script>

<style lang="css" scoped>
</style>
