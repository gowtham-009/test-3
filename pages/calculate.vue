<template>
    <div class="main-container w-100" :style="{height: deviceHeight + 'px'}" >
      <div class="w-100 boxex-1":style="{height:boxex1Height + 'px'}" >
        <logo/>
      </div>
      <div class="w-100 boxex-2":style="{height:boxex2Height + 'px'}" >
        <v-form>
            <v-container class="pa-0">
                <v-row no-gutters>
                <v-col cols="12" >
                    <v-sheet class="pa-1">
                    <p class="text-center font-weight-bold text-h6 text-blue mb-3">Enter Closing Details SF-AA-0020</p>

                    <v-row no-gutters>
                        <v-col cols="5" >
                            <v-sheet class="pa-1">
                                <v-text-field
                                    v-model="loannumber"
                                    :counter="10"
                                    :rules="loannumberRules"
                                    label="Loan_Number:"
                                    placeholder="SF-AA-0020"
                                    hide-details
                                    required
                                    class="w-100"
                                    ></v-text-field>
                            </v-sheet>
                        </v-col>
                        <v-col cols="7" >
                            <v-sheet class="pa-1">
                                <v-text-field
                                    v-model="loantyps"
                                    :counter="10"
                                    :rules="loantypeRules"
                                    label="Loan Type:"
                                    placeholder="Gold"
                                    hide-details
                                    required
                                    class="w-100"
                                    ></v-text-field>
                            </v-sheet>
                        </v-col>
                        <v-col cols="5" class="pa-0" >
                            <v-sheet class="pa-1">
                                <v-date-input label="Loan Date:" prepend-icon=""></v-date-input>
                            </v-sheet>
                        </v-col>
                        <v-col cols="7" >
                            <v-sheet class="pa-1">
                                <v-text-field
                                    v-model="loanvalue"
                                    :counter="10"
                                    :rules="loanvalueRules"
                                    label="Loan value:"
                                    placeholder="0000"
                                    hide-details
                                    required
                                    class="w-100"
                                    ></v-text-field>
                            </v-sheet>
                        </v-col>
                        </v-row>

                    </v-sheet>
                </v-col>

                <v-col cols="12" >
                    <v-sheet class="pa-1">
                        <v-row no-gutters>
                            <v-col cols="5">
                                <v-sheet class="pa-1 d-flex align-end" >
                                    <v-date-input label="Last Date:" prepend-icon=""></v-date-input>
                                </v-sheet>
                            </v-col>
                            <v-col cols="7">
                                <v-sheet class="pa-1" >
                                <v-text-field
                                    v-model="nan"
                                    :counter="10"
                                    :rules="nanRules"
                                    
                                 
                                    hide-details
                                    required
                                    class="w-100"
                                    ></v-text-field>
                                    <v-btn class="bg-indigo text-white" @click="sheet = !sheet" block>Total 7946.2</v-btn>
                                </v-sheet>
                            </v-col>
                            </v-row>
                    </v-sheet>
                </v-col>

                <v-col cols="12" class="pa-1" >
                    <v-sheet>
                        <v-row no-gutters class="pa-0">
                            <v-col cols="5" class="pa-0">
                                <v-sheet class="pa-0" >

                                    <v-col cols="12" class="pa-0">
                                        <v-sheet class="pa-1" >
                                        <span>Collected Extra:</span><br>
                                        <span>19955.10:</span>
                                        </v-sheet>
                                    </v-col>

                                    <v-col cols="12" class="pa-0 mt-2">
                                        <v-sheet class="pa-1" >
                                            <span>Intrest:</span><br>
                                            <span>19955.10:</span>
                                        </v-sheet>
                                    </v-col>

                                    <v-col cols="12" class="pa-0 mt-2">
                                        <v-sheet class="pa-1" >
                                            <span>Book Value:</span><br>
                                            <span>7555.10:</span>
                                        </v-sheet>
                                    </v-col>

                                </v-sheet>
                            </v-col>
                            <v-col cols="7">
                                <v-sheet class="pa-0" >
                                    
                                    <v-col cols="12" class="pa-0">
                                        <v-sheet class="pa-1" >
                                            <v-text-field
                                                v-model="nan"
                                                :counter="10"
                                                :rules="nanRules"
                                                placeholder="-5600.00"
                                            
                                                hide-details
                                                required
                                                class="w-100"
                                                ></v-text-field>
                                        </v-sheet>
                                    </v-col>

                                    <v-col cols="12" class="pa-0">
                                        <v-sheet class="pa-1" >
                                            <v-text-field
                                                v-model="nan"
                                                :counter="10"
                                                :rules="nanRules"
                                                placeholder="-5600.00"
                                            
                                                hide-details
                                                required
                                                class="w-100"
                                                ></v-text-field>
                                        </v-sheet>
                                    </v-col>

                                    <v-col cols="12" class="pa-0">
                                        <v-sheet class="pa-1" >
                                            <v-text-field
                                                v-model="nan"
                                                :counter="10"
                                                :rules="nanRules"
                                                placeholder="000"
                                            
                                                hide-details
                                                required
                                                class="w-100"
                                                ></v-text-field>
                                        </v-sheet>
                                    </v-col>

                                </v-sheet>
                            </v-col>
                            </v-row>
                    </v-sheet>
                </v-col>
                
                <v-col cols="12" >
                    <v-sheet class="pa-1">
                        <v-row no-gutters>
                            <v-col cols="5">
                                <v-sheet class="pa-1" >
                                <span>Office Book:</span><br>
                                <span>0.000:</span>
                                </v-sheet>
                            </v-col>
                            <v-col cols="7">
                                <v-sheet class="pa-1" >
                                    <v-text-field
                                    v-model="nan"
                                    :counter="10"
                                    :rules="nanRules"
                                    placeholder="000"
                                
                                    hide-details
                                    required
                                    class="w-100"
                                    ></v-text-field>
                                </v-sheet>
                            </v-col>
                            </v-row>
                    </v-sheet>
                </v-col>
                
                </v-row>
            </v-container>
        </v-form>
      </div>
  
      <div class="w-100 d-flex ga-2 pa-1 align-center" :style="{height:boxex3Height + 'px'}" >
        <div class="text-center w-100 pa-0" >
    <v-btn
      class="bg-indigo"
      text="7946.2"
      @click="sheet = !sheet"
      block
    ></v-btn>
    <v-bottom-sheet v-model="sheet" class="pa-0" >
      <v-card class="pa-0" :style="{height: tabHeight + 'px'}  ">
        <div class="tabs-container">
      <div class="tabs d-flex w-100 pa-2">
        <v-row no-gutters>
          <v-col class="pa-1 d-flex justify-center align-center" >
            <v-btn
              block
              class="grow-1"
              style="font-size: 15px"
              size="x-large"
              :class="{'active': activeTab === 0, 'custom-btn': true}"
              @click="activeTab = 0"
            >
              Weekly<br>Details
            </v-btn>
          </v-col>
          <v-col class="pa-1 d-flex justify-center align-center" >
            <v-btn
               class="grow-1"
               style="font-size: 15px"
               size="x-large"
              block
              :class="{'active': activeTab === 1, 'custom-btn': true}"
              @click="activeTab = 1"
            >
              Monts<br>20.40
            </v-btn>
          </v-col>
          <v-col class="pa-1 d-flex justify-center align-center" >
            <v-btn
             class="grow-1"
             style="font-size: 15px"
             size="x-large"
              block
              :class="{'active': activeTab === 2, 'custom-btn': true}"
              @click="activeTab = 2"
            >
              Intrest<br>₹1234.00
            </v-btn>
          </v-col>
          <v-col class="pa-1 d-flex justify-center align-center" >
            <v-btn
             class="grow-1"
             style="font-size: 15px"
             size="x-large"
              block
              :class="{'active': activeTab === 3, 'custom-btn': true}"
              @click="activeTab = 3"
            >
              Collect<br>1234.00
            </v-btn>
          </v-col>
        </v-row>
      </div>
      <div class="tab-content" v-show="activeTab === 0">
        
            <v-card-text class="pa-2">
              <v-card rounded="0"  flat>
                <v-window v-model="onboarding">
                  <v-window-item :value="1">
                    <v-card class="d-flex justify-center align-center">
                      <div class="w-100 d-flex flex-column pa-1 ga-2 bg-grey-lighten-3">
                        <div class="w-100">
                          <div class="w-100 pa-2 d-flex justify-space-between">
                            <span>Loan Item</span>
                            <span class="d-flex justify-center"><v-icon class="text-yellow" icon="mdi-circle"></v-icon>3.500g</span>
                          </div>
                          <div class="w-100 pa-2">
                            <span>Ring</span><br>
                            <span>Ring</span>
                          </div>
                        </div>
                        <div class="w-100 d-flex justify-center align-center pa-10" style="border: 1px solid grey; border-radius: 10px">
                          <img src="~/assets/image/apple.png" alt="pic-1" width="100" height="100">
                        </div>
                      </div>
                    </v-card>
                  </v-window-item>
                  <v-window-item :value="2">
                    <v-card class="d-flex justify-center align-center">
                      <div class="w-100 pa-2 d-flex flex-column ga-2 bg-grey-lighten-3">
                        <div class="w-100">
                          <div class="w-100">
                            <p class="text-black font-weight-bold text-h">Name & Address</p>
                            <p>ABCDE, 37, Main Street,<br> Thiruvaiyar, Thanjavur<br>Thanjavur<br>Thanjavur</p>
                          </div>
                  
                        </div>
                        <div class="w-100 d-flex justify-center align-center pa-10" style="border: 1px solid grey; border-radius: 10px">
                          <img src="~/assets/image/apple.png" alt="pic-1" width="100" height="100">
                        </div>
                      </div>
                    </v-card>
                  </v-window-item>
                  <v-window-item :value="3">
                    <v-card class="d-flex justify-center align-center">
                      <div class="w-100 d-flex flex-column ga-2 pa-2 bg-grey-lighten-3">
                        <div class="w-100">
                          <div class="w-100">
                            <p class="text-black font-weight-bold text-h">ID Proof Details</p>
                            <p>Aadhaar<br>XXXX XXXX 1234</p>
                          </div>
                  
                        </div>
                        <div class="w-100 d-flex justify-center align-center pa-10" style="border: 1px solid grey; border-radius: 10px">
                          <img src="~/assets/image/apple.png" alt="pic-1" width="100" height="100">
                        </div>
                      </div>
                    </v-card>
                  </v-window-item>
                  <!-- Add more v-window-item elements as needed -->
                </v-window>

                <v-card-actions class="d-flex justify-center" >
                  <v-item-group v-model="onboarding" class="text-center" mandatory >
                    <v-item v-for="n in length" :key="`btn-${n}`" v-slot="{ isSelected, toggle }" :value="n">
                      <v-btn :variant="isSelected ? 'outlined' : 'text'" icon="mdi-record" @click="toggle"></v-btn>
                    </v-item>
                  </v-item-group>
                </v-card-actions>
              </v-card>
            </v-card-text>
         

      </div>
      <div class="tab-content" v-show="activeTab === 1">
        <v-card class="bg-grey-lighten-3">
            <v-card-text class="pa-1">
              <v-container class="pa-2">
                  <v-row no-gutters>
                    <v-col cols='12' >
                      <v-sheet class="pa-2 rounded-lg">
                        <div class="w-100 d-flex justify-space-between">
                          <p class="font-weight-bold ">Today Date</p>
                          <p class="font-weight-bold ">11-Jul-2024</p>
                        </div>
                        <div class="w-100 mt-2 d-flex justify-space-between">
                          <p class="font-weight-bold ">Loan Date</p>
                          <p class="font-weight-bold ">11-Jun-2024</p>
                        </div>
                      </v-sheet>
                    </v-col>
                    <v-col cols='12' class="mt-2" >
                      <v-sheet class="pa-2 rounded-lg">
                        <div class="w-100 d-flex justify-space-between">
                          <p class="font-weight-bold ">Difference</p>
                          <p class="font-weight-bold ">647</p>
                        </div>
                        <div class="w-100 d-flex justify-space-between">
                          <p class="font-weight-bold ">In Days</p>
                          <p class="font-weight-bold ">Days</p>
                        </div>
                      </v-sheet>
                    </v-col>
                  </v-row>

                  <v-row no-gutters>
                    <v-col cols='12' class="mt-2 ">
                      <v-sheet class="pa-2 rounded-lg">
                        <div class="w-100 d-flex justify-center align-center">
                          <p class="font-weight-bold ">That is 21 Months & 12 Days</p>
                        </div>
                      </v-sheet>
                    </v-col>
                  </v-row>
                  <v-row no-gutters class="mt-2">
                    <v-col cols='6' class="ga-1">
                        <v-col cols='12' class="pa-2 rounded-lg bg-white" >
                          <p class="font-weight-bold">Rounded<br>Months</p>
                        </v-col>
                        <v-col cols='12' class="pa-2 rounded-lg mt-2 bg-white" >
                          <p class="font-weight-bold">Advance<br>Months</p>
                        </v-col>
                    </v-col>
                    <v-col cols='6' class="" style=" padding-left: 8px" >
                        <div class="d-flex rounded-lg pa-1 flex-column bg-white justify-end align-end justify-space-between ">
                          <p class="text-h4 font-weight-bold">20.40</p>
                        <p class="text-h4 font-weight-bold mt-8">1.00</p>
                        </div>
                      </v-col>
                  </v-row>
                    <v-row no-gutters>
                    <v-col cols="12 pa-1 mt-2 d-flex ga-1" >
                     
                    <div class="w-100 bg-indigo rounded-lg pa-2" style="flex:1">
                      <p class="font-weight-bold text-h6">Total<br>Months</p>
                    </div>
                    <div class="w-100 bg-indigo rounded-lg pa-2 d-flex justify-end align-center" style="flex:1">
                      <p class="font-weight-bold text-h5 text-end">20.40</p>
                    </div>
                
                    </v-col>
                  </v-row>
                </v-container>
            </v-card-text>
          </v-card>

      </div>
      <div class="tab-content" v-show="activeTab === 2">
        <v-card >
            <v-card-text class="pa-0 bg-grey-lighten-3">
              <v-card rounded="0"  class="bg-grey-lighten-3">
                  <v-window v-model="onboarding" >
                    <v-window-item :value="1" class="pa-1">
                      <v-container class="pa-2">
                <v-row no-gutters>
                  <v-col cols='12' class=" pa-1 rounded-lg bg-white" >
                    <div class="w-100 d-flex justify-space-between">
                      <p class="font-weight-bold ">Monthly Intrest</p>
                      <p class="font-weight-bold ">For 6000.00</p>
                    </div>
                    <div class="w-100 d-flex justify-space-between">
                      <p class="font-weight-bold text-h5 ">@12%</p>
                      <p class="font-weight-bold text-h5">60.00</p>
                    </div>
                  </v-col>
                  <v-col cols='12' class="pa-2 rounded-lg mt-2 bg-white">
                    <div class="w-100 d-flex justify-space-between">
                      <p class="font-weight-bold ">A) For</p>
                      <p class="font-weight-bold ">(60 x 12)</p>
                    </div>
                    <div class="w-100 d-flex justify-space-between">
                      <p class="font-weight-bold text-h6 ">12 Months</p>
                      <p class="font-weight-bold text-h5">720.00</p>
                    </div>
                  </v-col>
                  <v-col cols='12' class="pa-2 rounded-lg mt-2 bg-white">
                    <div class="w-100 d-flex justify-space-between">
                      <p class="font-weight-bold ">Monthly Intrest</p>
                      <p class="font-weight-bold ">For 6000.00</p>
                    </div>
                    <div class="w-100 d-flex justify-space-between">
                      <p class="font-weight-bold text-h5 ">@18%</p>
                      <p class="font-weight-bold text-h5">90.00</p>
                    </div>
                  </v-col>
                  <v-col cols='12' class="pa-2 rounded-lg mt-2 bg-white">
                    <div class="w-100 d-flex justify-space-between">
                      <p class="font-weight-bold ">B) For</p>
                      <p class="font-weight-bold ">(90 x 12)</p>
                    </div>
                    <div class="w-100 d-flex justify-space-between">
                      <p class="font-weight-bold text-h6 ">12 Months</p>
                      <p class="font-weight-bold text-h5">1080.00</p>
                    </div>
                  </v-col>
                  <v-col cols='12' class="pa-2 rounded-lg mt-5 d-flex ga-1 bg-white">
                    <div class="w-100 bg-indigo pa-2" style="flex:1">
                      <p class="font-weight-bold text-h6">Total (A+B)<br>Intrest</p>
                    </div>
                    <div class="w-100 bg-indigo pa-2 d-flex justify-end align-center" style="flex:1">
                      <p class="font-weight-bold text-h5">1800.00</p>
                    </div>
                  </v-col>
                </v-row>
              </v-container>
                    </v-window-item>
                    <v-window-item :value="2" class="pa-1">
                      <v-container class="pa-2">
                <v-row no-gutters>
                  <v-col cols='12' class="pa-2 rounded-lg bg-white" >
                    <div class="w-100  d-flex justify-space-between">
                      <p class="font-weight-bold ">Monthly Intrest</p>
                      <p class="font-weight-bold ">For 6000.00</p>
                    </div>
                    <div class="w-100 d-flex justify-space-between">
                      <p class="font-weight-bold text-h5 ">@12%</p>
                      <p class="font-weight-bold text-h5">60.00</p>
                    </div>
                  </v-col>
                  <v-col cols='12' class="pa-2 rounded-lg mt-2 bg-white" >
                    <div class="w-100 d-flex justify-space-between">
                      <p class="font-weight-bold ">For</p>
                      <p class="font-weight-bold ">(60 x 12)</p>
                    </div>
                    <div class="w-100 d-flex justify-space-between">
                      <p class="font-weight-bold text-h6 ">12 Months</p>
                      <p class="font-weight-bold text-h5">720.00</p>
                    </div>
                  </v-col>
                  
                 
                  <v-col cols='12' class="pa-2 rounded-lg mt-5 d-flex ga-1 bg-white" >
                    <div class="w-100 bg-indigo pa-2" style="flex:1">
                      <p class="font-weight-bold text-h6">Total<br>Intrest</p>
                    </div>
                    <div class="w-100 bg-indigo pa-2 d-flex justify-end align-center" style="flex:1">
                      <p class="font-weight-bold text-h5">720.00</p>
                    </div>
                  </v-col>
                </v-row>
              </v-container>
                    </v-window-item>
                    <!-- Add more v-window-item elements as needed -->
                  </v-window>

                  <v-card-actions class="d-flex justify-center pa-0 mt-0" >
                    <v-item-group v-model="onboarding" class="text-center" mandatory >
                      <v-item v-for="n in length_t" :key="`btn-${n}`" v-slot="{ isSelected, toggle }" :value="n">
                        <v-btn :variant="isSelected ? 'outlined' : 'text'" icon="mdi-record" @click="toggle"></v-btn>
                      </v-item>
                    </v-item-group>
                  </v-card-actions>
                </v-card>
            </v-card-text>
          </v-card>

      </div>
      <div class="tab-content" v-show="activeTab === 3">
        <v-card >
            <v-card-text class="bg-grey-lighten-3 pa-1">
              <v-container class="pa-2">
                <v-row no-gutters>
                  <v-col cols='12' class="pa-2 bg-white rounded-lg" >
                    <div class="w-100 d-flex justify-space-between">
                      <p class="font-weight-bold ">Loan<br>Amount</p>
                      <p class="font-weight-bold text-h5">6000.00</p>
                    </div>
                  </v-col>
                  <v-col cols='12' class="pa-2 mt-2 bg-white rounded-lg">
                    <div class="w-100 d-flex justify-space-between">
                      <p class="font-weight-bold ">Intrest<br>Amount</p>
                      <p class="font-weight-bold text-h5">720.00</p>
                    </div>
                  </v-col>
                  
                 
                  <v-col cols='12' class="pa-2 mt-5 d-flex ga-1 bg-white rounded-lg">
                    <div class="w-100 bg-indigo pa-2" style="flex:1">
                      <p class="font-weight-bold text-h6">Total<br>Intrest</p>
                    </div>
                    <div class="w-100 bg-indigo pa-2 d-flex justify-end align-center" style="flex:1">
                      <p class="font-weight-bold text-h5">6720.00</p>
                    </div>
                  </v-col>
                </v-row>
              </v-container>
            </v-card-text>
          </v-card>
      </div>
    </div>
      </v-card>
      </v-bottom-sheet>
  </div>
    <div class="w-100">
      <v-btn class="bg-green text-white" @click="dialog = true" block>Submit & Close</v-btn>
      <v-dialog
  v-model="dialog"
  width="auto"
    >
      <v-card
        max-width="400"
        prepend-icon="mdi-update"
        title="Do You Want Save and Edit?"
      >
        <template v-slot:actions>
         <div class="w-100 pa-1 d-flex ga-2 justify-end">
          <v-btn
            class=" bg-yellow"
            text="Edit"
            @click="dialog = false"
          ></v-btn>
          <v-btn
            class=" bg-indigo"
            text="Save"
            @click="savebtn"
          ></v-btn>
         </div>
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
        tabHeight:0,
        sheet: false,
        activeTab: 0,
        onboarding: 1,
        length:3,
        length_t:2,
        navtabHeight:0
      
  
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
        this.boxex3Height = Math.floor(this.boxex2Height * 0.05); // 6% of device height
        this.tabHeight = Math.floor(this.boxex2Height * 0.90);
        this.navtabHeight = Math.floor(this.tabHeight * 0.10);
       
      },
      savebtn(){
        alert("Data Successfully Saved.")
        this.$router.push('/dashboard')
      }
  
    }
  };
  </script>
  
  <style scoped>
  .boxex-2{
    overflow: hidden;
  overflow: scroll;
  }
  
  .bg-blue {
  background-color: blue !important;
}

.text-white {
  color: white !important;
}
.text-center {
  text-align: center;
}
.tabs-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    
   
  }
  
  .tabs {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
  gap: 5px;
  }
  
  /* Custom button styles */
  .custom-btn {
    background-color: #f1f1f1;
    border: none;
    padding: 10px 20px;
    margin: 5px;
    cursor: pointer;
    transition: background-color 0.3s;
  }
  
  .custom-btn:hover {
    background-color: #ddd;
  }
  
  .custom-btn.active {
    background-color: #007bff !important;
    color: white !important;
  }
  
  .tab-content {
    width: 100%;
    border: 1px solid #ccc;
    border-radius: 5px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  }
  </style>
  