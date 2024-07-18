<template>
    <div class="main-container w-100" :style="{height: deviceHeight + 'px'}">
      <div class="w-100 boxex-1":style="{height:boxex1Height + 'px'}">
        <logo/>
      </div>
      <div class="w-100 boxex-2 pa-2":style="{height:boxex2Height + 'px'}">
        <div class="loan-1 w-100 rounded-lg bg-indigo d-flex justify-center align-center pa-3" >
          <p class="text-white">Edit Intrest Record</p>
        </div>
        <div class="loan-2 w-100 d-flex  ga-10 justify-center align-center  " >
          <v-checkbox class="text-h6" label="Gold"></v-checkbox>
          <v-checkbox class="text-h6" label="Silver"></v-checkbox>
          <v-checkbox class="text-h6" label="Brass"></v-checkbox>
        </div>
  
        <div class="loan-3 w-100">
          <v-form>
            <v-row no-gutters>
                <v-col>
                    <v-sheet class="pa-2 ma-2" >
                        <label for="">Lower Limit</label>
                        <v-text-field
                        :counter="10"
                        placeholder="6.985"
                        hide-details
                        required
                        class="w-100"
                      ></v-text-field>
                    </v-sheet>
                </v-col>
                <v-col>
                    <v-sheet class="pa-2 ma-2" >
                        <label for="">Upper Limit</label>
                        <v-text-field
                        :counter="10"
                        placeholder="6668"
                        hide-details
                        required
                        class="w-100"
                      ></v-text-field>
                    </v-sheet>
                </v-col>
                </v-row>

                <v-row no-gutters>
                    <v-col cols="12">
                        <p class="text-blue font-weight-bold text-center">Discount 1st Year</p>
                    </v-col>
                <v-col>
                    <v-sheet class="pa-1" >
                        <label for="">Paisa</label>
                        <v-text-field
                        :counter="10"
                        placeholder="6.3"
                        hide-details
                        required
                        class="w-100"
                      ></v-text-field>
                    </v-sheet>
                </v-col>
                <v-col>
                    <v-sheet class="pa-1" >
                        <label for="">Intrest</label>
                        <v-text-field
                        :counter="10"
                        placeholder="1.1"
                        hide-details
                        required
                        class="w-100"
                      ></v-text-field>
                    </v-sheet>
                </v-col>
                <v-col>
                    <v-sheet class="pa-1" >
                        <label for="">OffbOOK</label>
                        <v-text-field
                        :counter="10"
                        placeholder="5.5452454548"
                        hide-details
                        required
                        class="w-100"
                      ></v-text-field>
                    </v-sheet>
                </v-col>
                </v-row>

                <v-row no-gutters>
                    <v-col cols="12">
                        <p class="text-blue font-weight-bold text-center">Elevated 2nd Year</p>
                    </v-col>
                <v-col>
                    <v-sheet class="pa-1" >
                        <label for="">Paisa 2</label>
                        <v-text-field
                        :counter="10"
                        placeholder="1/2/3/4/5/6/7"
                        hide-details
                        required
                        class="w-100"
                      ></v-text-field>
                    </v-sheet>
                </v-col>
                <v-col>
                    <v-sheet class="pa-1" >
                        <label for="">Intrest 2</label>
                        <v-text-field
                        :counter="10"
                        
                        hide-details
                        required
                        class="w-100"
                      ></v-text-field>
                    </v-sheet>
                </v-col>
                <v-col>
                    <v-sheet class="pa-1" >
                        <label for="">OffbOOK 2</label>
                        <v-text-field
                        :counter="10"
                       
                        hide-details
                        required
                        class="w-100"
                      ></v-text-field>
                    </v-sheet>
                </v-col>
                </v-row>

                <v-row no-gutters class="mt-3">
                <v-col>
                    <v-sheet class="pa-1 d-flex justify-center ga-2 pa-2">
                        <v-btn class="text-green " style="border: 1px solid green;">Update</v-btn>
                        <nuxt-link to="/admin" style="text-decoration: none;"><v-btn class="text-red" style="border: 1px solid red;">Cancel</v-btn></nuxt-link>
                    </v-sheet>
                </v-col>
                </v-row>
          </v-form>
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
        this.boxex1Height = Math.floor(this.deviceHeight * 0.10); // 10% of device height
        this.boxex2Height = Math.floor(this.deviceHeight * 0.90); // 90% of device height
        
      },
    }
  };
  </script>
  
  <style scoped>
  
  
  
  </style>
  