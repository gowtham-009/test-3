<template>
  <div class="main-container w-100" :style="{height: deviceHeight + 'px'}">
    <div class="w-100 boxex-1bg-grey-lighten-4 rounded-xl d-flex justify-center align-center":style="{height:boxex1Height + 'px'}">
      <logo/>
    </div>
    <div class="w-100 boxex-2 pa-2 d-flex justify-center":style="{height:boxex2Height + 'px'}">
      <v-form class="w-100 d-flex justify-center">
    <v-container class="w-100 d-flex justify-center">
      <v-row class="d-flex flex-column justify-space-between">
        <div class="w-100">
          <v-col cols="12">
          <v-text-field label="User ID" required></v-text-field>
        </v-col>
        <v-col cols="12">
          <v-text-field  label="Password" required></v-text-field>
        </v-col>
        <v-col cols="12" class="d-flex justify-center">
          <nuxt-link to="/" class="text-center" style="text-decoration: none;">Reset your Password</nuxt-link>
        </v-col>
       
        </div>
        <div class="w-100">
          <v-col cols="12">
          <nuxt-link to="/dashboard" style="text-decoration: none;">
            <v-btn block size="large" class="bg-indigo text-white text-h5 rounded-xl">Login</v-btn>
          </nuxt-link>
        </v-col>
        </div>
      </v-row>
    </v-container>

    <!-- <v-dialog v-model="dialog" max-width="400">
      <v-card>
        <v-card-title>Updat Status</v-card-title>
        <v-card-text>
          {{ dialogMessage }}
        </v-card-text>
        <v-card-actions>
          <v-btn color="primary" @click="dialog = false">Close</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog> -->
  </v-form>

  </div>
  </div>
</template>

<script>
import logo from '~/components/logo.vue'
export default {
  components:{
logo
  },
  data() {
    return {
      deviceWidth: 0,
      deviceHeight: 0,
      boxex1Height: 0,
      boxex2Height: 0,
      

    };
  },
  mounted() {
    this.updateDeviceDimensions(); // Initial call to set dimensions on component mount
    window.addEventListener('resize', this.updateDeviceDimensions); // Listen for window resize events
  },
  beforeDestroy() {
    window.removeEventListener('resize', this.updateDeviceDimensions); // Clean up: remove resize event listener
  },
  methods: {
    updateDeviceDimensions() {
      this.deviceWidth = window.innerWidth; // Update device width
      this.deviceHeight = window.innerHeight; // Update device height

      // Calculate heights for each boxex based on percentages
      this.boxex1Height = Math.floor(this.deviceHeight * 0.20); // 20% of device height
      this.boxex2Height = Math.floor(this.deviceHeight * 0.80); // 80% of device height 
    },
  }
};
</script>

<style scoped>



</style>
