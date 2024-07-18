<template>
  <div>
   <div class="main_container w-100" :style="{height: deviceHeight + 'px'}">
        <div class="box-1 w-100" :style="{height:boxex1Height + 'px'}">
          <logo/>
        </div>
        <div class="box-2 w-100 d-flex flex-column" :style="{height:boxex2Height + 'px'}">
          <div class="w-100 d-flex">
            <div class="w-100">
                  <v-btn variant="plain" class="text-blue font-weight-bold text-h6 " block>New User</v-btn>
                </div>
                <div class="w-100">
                  <nuxt-link to="/search2" style="text-decoration: none;"><v-btn variant="plain" class="bg-deep-purple-accent-3 text-white font-weight text-h6" block>Search User</v-btn></nuxt-link>
                </div>
          </div>
          <div class="w-100">
            <span class="text-body-2" style="padding-left: 6px;">Proof Type</span>
                <v-sheet class="w-100 pa-0">
                  <v-chip-group selected-class="text-white bg-blue pa-2" style="padding-left: 8px;" column>
                    <v-chip
                      variant="outlined"
                      class="text-black text-caption"
                      v-for="tag in tags"
                      :key="tag"
                    >
                      {{ tag }}
                    </v-chip>
                  </v-chip-group>
                  <div class="horizontal-line w-100 mt-1"></div>
                </v-sheet>
          </div>
          <div class="w-100 d-flex flex-column" style="flex: 1;">
                 <v-form>
                <v-container class="pa-1">
                  <v-row class="d-flex flex-column ga-1 ">
                    <v-col
                      cols="12"
                    >
                      <v-text-field
                        v-model="proofid"
                        :counter="10"
                        :rules="proofRules"
                        label="Proof ID / Number"
                        placeholder="English / தமிழ்"
                        hide-details
                        required
                        class="w-100"
                      ></v-text-field>
                    </v-col>

                    <v-col
                      cols="12"
                    
                    >
                      <v-text-field
                        v-model="name"
                        :counter="10"
                        :rules="nameRules"
                        label="Name"
                        placeholder="English / தமிழ்"
                        hide-details
                        required
                      ></v-text-field>
                    </v-col>


                    <v-col
                      cols="12"
                    
                    >
                    <v-textarea
                      append-inner-icon="mdi-map-marker"
                      label="Address"
                      placeholder="English / தமிழ்"
                    ></v-textarea>
                    </v-col>

                    <v-col
                      cols="12"
                      style="margin-top: -17px;"
                    >
                      <v-text-field
                        v-model="place"
                        :counter="10"
                        :rules="place"
                        label="Place"
                        placeholder="English / தமிழ்"
                        hide-details
                        required
                        class="w-100"
                      ></v-text-field>
                    </v-col>
                    <v-col class="d-flex ga-2"
                      cols="12"
                      >
                      <div class="w-50 d-flex flex-column pa-2">
                        <h5>Person</h5>
                        <div class="card pa-2 d-flex flex-column justify-center align-center ga-3 rounded-lg bg-grey-lighten-3 w-100">
                          <v-icon icon="mdi-file-upload" class="text-h4"></v-icon>
                          <p class="text-center">Drag and drop <br> File Here</p>
        
                          <v-btn   class="bg-red rounded-lg text-white">Browser File</v-btn>
                        </div>
                      </div>
                      <div class="w-50 d-flex flex-column pa-2">
                        <h5>Person</h5>
                        <div class="card pa-2 d-flex flex-column justify-center align-center ga-3 rounded-lg bg-grey-lighten-3 w-100">
                          <v-icon icon="mdi-file-upload" class="text-h4"></v-icon>
                          <p class="text-center">Drag and drop <br> File Here</p>
        
                          <v-btn   class="bg-red rounded-lg text-white ">Browser File</v-btn>
                        </div>
                      </div>
                  </v-col>
                  </v-row>  
                </v-container>
                </v-form>
          </div>
         

        </div>
        <div class="w-100 d-flex ga-2 justify-center align-center pa-2" :style="{height:boxex3Height + 'px'}">
          <div class="w-100"><v-btn class="bg-yellow text-black" block>Reset</v-btn></div>
          <div class="w-100"><nuxt-link to="/new_loan" style="text-decoration: none;"><v-btn class="bg-green text-white" block>Next</v-btn></nuxt-link></div>
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
      tags: [
        'Aadhaar', 'Voter ID', 'Driving License', 'Ration Card',
        'Bank Passbook', 'Passport', 'Other', 'Digilocker'
      ],
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
      this.boxex3Height = Math.floor(this.deviceHeight * 0.05); // 5% of device height
     
    },
    

  }
};
</script>

<style scoped>

.box-2{
  overflow: hidden;
  overflow: scroll;
}

</style>
