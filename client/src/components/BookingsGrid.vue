<template lang="html">
  <div>
    <booking v-for="(booking, index) in bookings" v-bind:booking="booking" v-bind:index="index"/>
  </div>
</template>



<script>
import Booking from '@/components/Booking.vue';
import HotelService from '@/services/HotelService.js';


export default {
  name: 'bookings-grid',
  
  data(){
    return {
      bookings: []
    }
  },
  
  components: {
    'booking': Booking
  },
  
  methods(){
    fetchBookings = function(){
      HotelService.INSERTNAMEOFFUNCTIONHERE!!!!!!!!()
      .then((bookings) => this.bookings = bookings);
    }
  },
  
  mounted(){
    this.fetchBookings();
    
    eventBus.$on('refresh-bookings', this.fetchBookings());
  }
}
</script>



<style lang="css" scoped>
</style>
