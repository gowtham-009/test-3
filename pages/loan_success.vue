<template>
    <div class="main-container w-100" :style="{height: deviceHeight + 'px'}">
      <div class="w-100 boxex-1":style="{height:boxex1Height + 'px'}">
        <logo/>
      </div>
      <div class="w-100 boxex-2":style="{height:boxex2Height + 'px'}">
         <div class="w-100 d-flex justify-center align-center pa-3">
            <h2 class="text-center">Loan Creation Success</h2>
         </div>
         <div class="w-100 mt-4 d-flex justify-center align-center">
            <h2 class="text-center">Text Summary of all input boxes</h2>
         </div>
      </div>
  
      <div class="w-100 d-flex ga-2 pa-2 align-center" :style="{height:boxex3Height + 'px'}">
        <div class="w-100"><nuxt-link to="/new_user" style="text-decoration: none;"><v-btn class="bg-yellow text-black" block>Reset</v-btn></nuxt-link></div>
          <div class="w-100">
            <v-btn @click="dialog = true" class="bg-green text-white" block>Insert</v-btn>
            <v-dialog
      v-model="dialog"
      width="auto"
    >
      <v-card
        max-width="400"
        prepend-icon="mdi-check"
        text="Your data has been Submitted in Database"
        title="Data Submission"
      >
        <template v-slot:actions>
          <v-btn
            class="ms-auto"
            text="Ok"
            @click="data_submission"
          ></v-btn>
        </template>
      </v-card>
    </v-dialog>
          </div>
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
        dialog: false,
        deviceWidth: 0,
        deviceHeight: 0,
        boxex1Height: 0,
        boxex2Height: 0,
        boxex3Height: 0,
      
        
  
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
        this.boxex1Height = Math.floor(this.deviceHeight * 0.10); // 10% of device height
        this.boxex2Height = Math.floor(this.deviceHeight * 0.85); // 85% of device height
        this.boxex3Height = Math.floor(this.deviceHeight * 0.05); // 6% of device height
      },
      data_submission(){
        alert("Data Saved")
        this.$router.push('/dashboard')
      }
  
    }
  };
  </script>
  
  <style scoped>
  
  
  </style>
  