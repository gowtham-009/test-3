<template>
    <div class="main-container w-100" :style="{height: deviceHeight + 'px'}">
      <div class="w-100 boxex-1 d-flex justify-center align-center" :style="{height: boxex1Height + 'px'}">
        <logo/>
      </div>
      <div class="w-100 boxex-2 d-flex flex-column" :style="{height: boxex2Height + 'px'}">
        <v-container class="pa-0 d-flex flex-column flex-grow-1">
          <v-row no-gutters class="flex-grow-1">
            <v-col class="d-flex">
              <nuxt-link to="/new_user" class="rounded-xl text-h4 text-white rounded-xl text-start pa-2 ma-2 d-flex justify-start align-start flex-grow-1 bg-green" style="text-decoration: none;">
            New<br>user
             
            </nuxt-link>
            </v-col>
            <v-col class="d-flex">
                <nuxt-link to="/new_loan" class="text-h4 text-start text-white rounded-xl pa-2 ma-2 flex-grow-1 bg-green" style="text-decoration: none;">New<br>Loan</nuxt-link>
            </v-col>
          </v-row>
          <v-row no-gutters class="flex-grow-1">
            <v-col class="d-flex">
                <nuxt-link to="/searchdata" class="text-h4 text-white rounded-xl pa-2 ma-2 d-flex justify-center align-center  flex-grow-1 bg-yellow" style="text-decoration: none;">Search & Close</nuxt-link>
            </v-col>
          </v-row>
          <v-row no-gutters class="flex-grow-1">
            <v-col class="d-flex">
              <nuxt-link to="/admin" class="text-h4 text-white rounded-xl pa-2 ma-2 d-flex justify-center align-center  flex-grow-1 bg-indigo" style="text-decoration: none;">Admin</nuxt-link>
            </v-col>
          </v-row>
          <v-row no-gutters class="flex-grow-1">
            <v-col class="d-flex">
                <nuxt-link to="" class="text-end text-h4 pa-2 ma-2 flex-grow-1 bg-red rounded-xl d-flex justify-end align-end">Ledger<br>Reports</nuxt-link>
            </v-col>
            <v-col class="d-flex">
              <nuxt-link to="" class="text-end text-h4 pa-2 ma-2 rounded-xl flex-grow-1 bg-red d-flex justify-end align-end">Balance<br>Check</nuxt-link>
                
            </v-col>
          </v-row>

          <v-row no-gutters class="flex-grow-1 d-flex justify-end">
            <v-col class="d-flex" cols="6">
                <nuxt-link to="/login" class="text-h4 text-white rounded-xl pa-2 ma-2 flex-grow-1 bg-black d-flex justify-end align-center" style="text-decoration: none;">Logout</nuxt-link>
            </v-col>
          </v-row>
        </v-container>
      </div>
    </div>
  </template>
  
  <script>
  import logo from '~/components/logo.vue'
  export default {
    components: {
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
      window.removeEventListener('resize', this.updateDeviceDimensions()); // Clean up: remove resize event listener
    },
    methods: {
      updateDeviceDimensions() {
        this.deviceWidth = window.innerWidth; // Update device width
        this.deviceHeight = window.innerHeight; // Update device height
  
        // Calculate heights for each box based on percentages
        this.boxex1Height = Math.floor(this.deviceHeight * 0.10); // 10% of device height
        this.boxex2Height = Math.floor(this.deviceHeight * 0.89); // 89% of device height
      },
    }
  };
  </script>
  
  <style scoped>
  .main-container {
    width: 100%;
  }
  
  .boxex-1 {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  
  .v-container {
    display: flex;
    flex-direction: column;
    height: 100%;
  }
  
  .v-row {
    display: flex;
    flex-grow: 1;
  }
  
  .v-col {
    display: flex;
  }
  
  .v-sheet {
    display: flex;
    flex-grow: 1;
    border-radius: 10px;
  }
  </style>
  