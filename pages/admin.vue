<template>
  <div class="main-container w-100" :style="{ height: deviceHeight + 'px' }">
    <div class="w-100 d-flex justify-center align-center" :style="{ height: box1Height + 'px' }">
      <logo/>
    </div>
    <div class="w-100" :style="{ height: box2Height + 'px' }" >
      <v-card class="pa-0">
      <v-tabs v-model="tab" align-tabs="center" class="bg-white">
        <v-tab
          value="tab-1"
          :class="{'active-tab': tab === 'tab-1'}"
          @mouseover="hoverTab('tab-1')"
          @mouseleave="hoverTab('')"
          :style="{'background-color': hoveredTab === 'tab-1' ? 'blue' : '', 'color': hoveredTab === 'tab-1' ? 'white' : ''}"
          class="rounded-lg"
        >
          Saved
        </v-tab>
        <v-tab
          value="tab-2"
          :class="{'active-tab': tab === 'tab-2'}"
          @mouseover="hoverTab('tab-2')"
          @mouseleave="hoverTab('')"
          :style="{'background-color': hoveredTab === 'tab-2' ? 'blue' : '', 'color': hoveredTab === 'tab-2' ? 'white' : ''}"
           class="rounded-lg"
        >
          Add
        </v-tab>
        <v-tab
          value="tab-3"
          :class="{'active-tab': tab === 'tab-3'}"
          @mouseover="hoverTab('tab-3')"
          @mouseleave="hoverTab('')"
          :style="{'background-color': hoveredTab === 'tab-3' ? 'blue' : '', 'color': hoveredTab === 'tab-3' ? 'white' : ''}"
           class="rounded-lg"
        >
          One Time
        </v-tab>
      </v-tabs>

      <v-tabs-window v-model="tab">
        <v-tabs-window-item value="tab-1">
         <v-card>
            <v-container class="pa-1">
              <v-row no-gutters>
                <v-col cols="12" class="pa-1" >
                  <v-select
                  :items="items"
                  label="Filter"
                   variant="solo-filled"
                ></v-select>

                </v-col>
                <v-col cols="12" class="pa-1" >
                  <span class="text-h6 text-indigo">Loan Type</span>
                  <v-radio-group v-model="inline" inline class="d-flex justify-center" >
                    <v-radio label="All" value="All" color="blue"></v-radio>
                    <v-radio label="Brass" value="Brass" color="blue"></v-radio>
                    <v-radio label="Gold" value="Gold" color="blue"></v-radio>
                  </v-radio-group>
                </v-col>
                <v-col cols="12" class="pa-1" >
                  <v-row no-gutters>
                    <v-col cols="6" class="pa-1">
                      <v-sheet>
                        <label for="">Select Low Limit</label>
                        <v-select
                          :items="items"
                          label="All Place"
                          variant="solo-filled"
                        ></v-select>
                      </v-sheet>
                    </v-col>
                    <v-col cols="6" class="pa-1">
                      <v-sheet>
                        <label for="">Select Upper Limit</label>
                        <v-select
                          :items="items"
                          label="All Place"
                          variant="solo-filled"
                        ></v-select>
                      </v-sheet>
                    </v-col>
                  </v-row>
                </v-col>
                <v-col cols="12" class="pa-1" >
                  <v-btn class="text-white bg-indigo" block>Search</v-btn>
                </v-col>
              </v-row>
            </v-container>

            <v-row no-gutters>
               <v-col cols="12" class="pa-2">
                <v-sheet class="w-100 pa-1 d-flex flex-column">
                  <div class="w-100 d-flex justify-space-between" >
                  <p class="text-indigo font-weight-bold">Brass</p>
                  <p class="text-indigo font-weight-bold">From 6,985-to-6668</p>
                </div>
                <div class="w-100 mt-1 d-flex justify-space-between" >
                  <span >1st Year</span>
                  <span >Total 6.3 Paisa</span>
                </div>
                <div class="w-100 d-flex justify-space-between" >
                  <span>split of 6.3 Paisa is</span>
                  <span>1.1 Int +3.05 Off</span>
                </div>
                <div class="w-100 mt-1 d-flex justify-space-between" >
                  <span>2nd year+</span>
                  <span>Total Paisa</span>
                </div>
                <div class="w-100 d-flex justify-space-between" >
                  <span>Split of paisa is</span>
                  <span>Int + Off</span>
                </div>
                </v-sheet>
               </v-col>
               <v-col cols="12" class="pa-2 d-flex ga-2">
                  <div class="w-100"><nuxt-link to="/editall" style="text-decoration: none;"><v-btn class="bg-red text-white" block>Edit</v-btn></nuxt-link></div>
                  <div class="w-100"><nuxt-link><v-btn class="bg-blue text-white" block>Calculate</v-btn></nuxt-link></div>
               </v-col>
            </v-row>
         </v-card>
        </v-tabs-window-item>

         <v-tabs-window-item  value="tab-2" v-if="tab === 'tab-2'">
            <v-container class="pa-1">
              <v-row no-gutters>
                  <v-col cols="12" class="pa-0" >
                    <p class="text-center text-indigo font-weight-bold">Add Intrest Record</p>
                    <v-row no-gutters class="">
                      <v-col cols="4" class="d-flex pa-0 justify-center"><v-checkbox class="text-h6" style="height: 40px" label="Gold"></v-checkbox></v-col>
                      <v-col cols="4" class="d-flex pa-0 justify-center"><v-checkbox class="text-h6" style="height: 40px" label="Silver"></v-checkbox></v-col>
                      <v-col cols="4" class="d-flex pa-0 justify-center"><v-checkbox class="text-h6" style="height: 40px" label="Brass"></v-checkbox></v-col>
                    </v-row>
                  </v-col>
                  <v-col cols="12" class="d-flex " >
                    <v-col>
                      <v-sheet  >
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
                      <v-sheet >
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
                  </v-col>
                  <v-col cols="12" class="pa-1 mt-1" >
                    <p class="text-indigo font-weight-bold text-center">Discount Intrest</p>
                    <v-container class="w-100 pa-0">
                      <v-row no-gutters>
                        <v-col class="pa-1" >
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
                        <v-col class="pa-1" >
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
                        <v-col class="pa-1" >
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

                    </v-container>
                  </v-col>
                  <v-col cols="12" class="pa-1 mt-1" >
                    <p class="text-indigo font-weight-bold text-center">Elevated Intrest</p>
                    <v-container class="w-100 pa-0">
                      <v-row no-gutters>
                        <v-col class="pa-1" >
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
                        <v-col class="pa-1" >
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
                        <v-col class="pa-1" >
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

                    </v-container>
                  </v-col>
                  <v-col cols="12" class="d-flex pa-2 ga-2 mt-3" >
                    <div class="w-100"><v-btn class="bg-yellow text-black" block>Reset</v-btn></div>
                    <div class="w-100"><nuxt-link to="" style="text-decoration: none;"><v-btn class="bg-green text-white" block>Insert</v-btn></nuxt-link></div>
                  </v-col>
              </v-row>
            </v-container>
        </v-tabs-window-item>

        <v-tabs-window-item value="tab-3" v-if="tab === 'tab-3'">
            <v-container class="pa-1">
              <v-row no-gutters>
                <v-col cols="12" class="pa-1" >
                  <p class="ma-1">[1] Extra 3 Days after 1 Month will be calculated as ?</p>
                  <v-row no-gutters>
                    <v-col cols="auto"><v-checkbox class="text-h6" style="height: 40px" label="Gold"></v-checkbox></v-col>
                    <v-col cols="auto"><v-checkbox class="text-h6" style="height: 40px" label="Silver"></v-checkbox></v-col>
                    <v-col cols="auto"><v-checkbox class="text-h6" style="height: 40px" label="Brass"></v-checkbox></v-col>
                  </v-row>
                  <div class="w-100 mt-2" style="border: 1px solid black;"></div>
                </v-col>
                <v-col cols="12" class="pa-1 mt-1" >
                  <v-row>
                    <v-col><p class="ma-1">[2] How many months of Initial <br> Interest Deducation?(Type in Months)</p></v-col>
                    <v-col> 
                      <v-text-field
                        :counter="10"
                        placeholder="1"
                        hide-details
                        required
                        class="w-100"
                      ></v-text-field>
                    </v-col>
                  </v-row>
                  <div class="w-100 mt-2" style="border: 1px solid black;"></div>
                </v-col>
                <v-col cols="12" class="pa-1 mt-1" >
                  <p class="ma-1">[3] Do you need value handover calculation?</p>
                  <v-row>
                    <v-col cols="auto"> <v-checkbox class="text-h6" style="height: 40px" label="Yes"></v-checkbox></v-col>
                    <v-col cols="auto"> <v-checkbox class="text-h6" style="height: 40px" label="No"></v-checkbox></v-col>
                  </v-row>
                  <div class="w-100 mt-2" style="border: 1px solid black;"></div>
                </v-col>
                <v-col cols="12" class="pa-1 mt-1" >
                  <p class="ma-1">[4] calculation Type?</p>
                  <v-row no-gutters class="d-flex">
                    <v-col cols="auto">
                      <v-checkbox class="text-h6" style="height: 40px" label="Discount"></v-checkbox>
                    </v-col>
                    <v-col cols="auto">
                      <v-checkbox class="text-h6" style="height: 40px" label="Discount+Elevated"></v-checkbox>
                    </v-col>
                    <v-col cols="auto">
                      <v-checkbox class="text-h6" style="height: 40px" label="Elevated"></v-checkbox>
                    </v-col>
                  </v-row>

                </v-col>
                <v-col cols="12" class="pa-2 mt-3" >
                  <v-btn class="bg-indigo text-white" block>Update</v-btn>
                </v-col>
              </v-row>
            </v-container>
        </v-tabs-window-item>
      </v-tabs-window>     
      </v-card>            
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
      box1Height:0,
      box2Height:0,
      tab: 'tab-1',
      hoveredTab: '', // Track the currently hovered tab
      items: ['Foo', 'Bar', 'Fizz', 'Buzz'],
      inline: null,
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
      this.box1Height=Math.floor(this.deviceHeight * 0.10); //this box1height 10%
      this.box2Height=Math.floor(this.deviceHeight * 0.90); //this box1height 90%

     
    },
    hoverTab(tab) {
      this.hoveredTab = tab; // Update the currently hovered tab
    },
  },
};
</script>

<style scoped>
.active-tab {
  background-color: blue !important;
  color: white !important;
}

</style>
