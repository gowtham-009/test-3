<template>
  <div class="main-container w-100" :style="{height: deviceHeight + 'px'}">
    <div class="w-100 boxex-1  d-flex justify-center align-center" :style="{height: boxex1Height + 'px'}">
      <logo/>
    </div>
    <div class="w-100 boxex-2 d-flex flex-column" :style="{height: boxex2Height + 'px'}">
      <div class="boxex  rounded-t-xl">
      <v-card class="rounded-t-xl">
        <v-tabs v-if="showMainContent" v-model="tab" align-tabs="center">
          <v-tab value="tab-1">Mobile Number</v-tab>
          <v-tab value="tab-2">Name</v-tab>
          <v-tab value="tab-3">ID</v-tab>
         
          
        </v-tabs>

        <v-tabs-window v-if="showMainContent" v-model="tab">
         
          
          <v-tabs-window-item value="tab-1" v-if="tab === 'tab-1'">
            <v-card>
              <v-sheet class="w-100 pa-2">
                <v-form @submit.prevent="phone_loan_search">
                  <v-text-field v-model="mobile" label="Mobile (type min 5 characters)"></v-text-field>
                  <v-btn class=" bg-deep-purple-accent-4" size="x-large" type="submit" block>Search</v-btn>
                </v-form>
              </v-sheet>

             <v-sheet class="w-100 pa-2 mt-2 bg-grey-lighten-5">
                  <v-card class="bg-grey-lighten-5  pa-2" variant="tonal">
                    <div class="w-100 d-flex">
                      <div class="w-100 d-flex justify-start align-center pa-1">
                        <p class="text-h6 text-blue font-weight-bold">SF-AA-0020</p>
                      </div>
                      <div class="w-100 d-flex justify-end align-center pa-1">
                        <p class="text-h6 text-blue font-weight-bold">5000</p>
                      </div>
                    </div>
                    <div class="w-100 d-flex">
                      <div class="w-100 d-flex justify-start flex-column pa-1">
                        <span class=" text-black ">Faf</span>
                        <span class=" text-black ">Disabled 2</span>
                      </div>
                      <div class="w-100 d-flex justify-end align-start pa-1">
                        <span class=" text-black ">12-feb-2022</span>
                      </div>
                    </div>
                    <div class="w-100 d-flex ga-2 align-center">
                      <div class="w-100"><v-btn class="bg-yellow text-black" block>Edit</v-btn></div>
                      <div class="w-100"><nuxt-link to="/calculate" style="text-decoration: none;"><v-btn class="bg-red text-white" block>Calculate</v-btn></nuxt-link></div>
                  </div>
                  </v-card>
                </v-sheet>

            </v-card>
          </v-tabs-window-item>

          <v-tabs-window-item value="tab-2" v-if="tab === 'tab-2'">
            <v-card>
              <v-sheet class="w-100 pa-2">
                <v-form @submit.prevent="namesearch" >
                  <v-text-field v-model="name" label="Name (type min 3 characters)"></v-text-field>
                  <v-text-field v-model="place" label="Place (type min 3 characters)"></v-text-field>
                  <v-btn class=" bg-deep-purple-accent-4" size="x-large" type="submit" block>Search</v-btn>
                </v-form>
              </v-sheet>
             <v-sheet class="w-100 pa-2 mt-2 bg-grey-lighten-5">
                  <v-card class="bg-grey-lighten-5  pa-2" variant="tonal">
                    <div class="w-100 d-flex">
                      <div class="w-100 d-flex justify-start align-center pa-1">
                        <p class="text-h6 text-blue font-weight-bold">SF-AA-0020</p>
                      </div>
                      <div class="w-100 d-flex justify-end align-center pa-1">
                        <p class="text-h6 text-blue font-weight-bold">5000</p>
                      </div>
                    </div>
                    <div class="w-100 d-flex">
                      <div class="w-100 d-flex justify-start flex-column pa-1">
                        <span class=" text-black ">Faf</span>
                        <span class=" text-black ">Disabled 2</span>
                      </div>
                      <div class="w-100 d-flex justify-end align-start pa-1">
                        <span class=" text-black ">12-feb-2022</span>
                      </div>
                    </div>
                    <div class="w-100 d-flex ga-2 align-center">
                      <div class="w-100"><v-btn class="bg-yellow text-black" block>Edit</v-btn></div>
                      <div class="w-100"><nuxt-link to="/calculate" style="text-decoration: none;"><v-btn class="bg-red text-white" block>Calculate</v-btn></nuxt-link></div>
                  </div>
                  </v-card>
                </v-sheet>
            </v-card>
          </v-tabs-window-item>


          <v-tabs-window-item value="tab-3">
            <v-card>
              <div class="main_id_box">
                <v-sheet class="w-100">
                  <div class="pa-2">
                    <v-chip-group selected-class="text-white bg-blue" column class="pa-2">
                      <v-chip
                        class="text-black "
                        v-for="tag in tags"
                        :key="tag"
                        @click="selectTag(tag)"
                        style="border: 1px solid black; background-color: whitesmoke;"
                      >
                        {{ tag }}
                      </v-chip>
                    </v-chip-group>
                  </div>
                </v-sheet>
                <v-sheet class="w-100 pa-2 mt-2">
                  <v-form @submit.prevent="toggleSearch">
                    <v-text-field
                      v-model="idnumber"
                      :rules="rules"
                      label="ID number last four characters"
                    ></v-text-field>
                    <v-btn class=" bg-deep-purple-accent-4" size="x-large" type="submit" block>Search</v-btn>
                  </v-form>
                </v-sheet>

                <v-sheet class="w-100 pa-2 mt-2 bg-grey-lighten-5">
                  <v-card class="bg-grey-lighten-5  pa-2" variant="tonal">
                    <div class="w-100 d-flex">
                      <div class="w-100 d-flex justify-start align-center pa-1">
                        <p class="text-h6 text-blue font-weight-bold">SF-AA-0020</p>
                      </div>
                      <div class="w-100 d-flex justify-end align-center pa-1">
                        <p class="text-h6 text-blue font-weight-bold">5000</p>
                      </div>
                    </div>
                    <div class="w-100 d-flex">
                      <div class="w-100 d-flex justify-start flex-column pa-1">
                        <span class=" text-black ">Faf</span>
                        <span class=" text-black ">Disabled 2</span>
                      </div>
                      <div class="w-100 d-flex justify-end align-start pa-1">
                        <span class=" text-black ">12-feb-2022</span>
                      </div>
                    </div>
                    <div class="w-100 d-flex ga-2 align-center">
                      <div class="w-100"><v-btn class="bg-yellow text-black" block>Edit</v-btn></div>
                      <div class="w-100"><nuxt-link to="/calculate" style="text-decoration: none;"><v-btn class="bg-red text-white" block>Calculate</v-btn></nuxt-link></div>
                  </div>
                  </v-card>
                </v-sheet>
              </div>
            </v-card>
          </v-tabs-window-item>

        </v-tabs-window>

        <!-- only show mobileloan class content -->
      <div class="mobile_container w-100 bg-white pa-2" v-if="showMobileContain">
        <h4 class="text-center">Search Results for Phone and loan</h4>
        <div class="name-contain w-100 d-flex ga-1 pa-2 mt-3">
          <div class="w-100 pa-2">
            <v-sheet>
              <v-form fast-fail @submit.prevent class="d-flex w-100 ga-2">
                <div class="form-field w-75">
                  <v-text-field v-model="mobileResult" label="Search result for phone"></v-text-field>
                </div>
                <div class="field-btn w-25 d-flex justify-center align-end">
                  <v-btn class="bg-yellow mb-5" size="x-large" type="submit" @click="editResult_mobile" block>Edit</v-btn>
                </div>
              </v-form>
            </v-sheet>
          </div>
        </div>
      </div>

      <!-- Only show namecontain class content -->
      <div class="namecontain bg-white" v-if="showNameContain">
        <h4 class="text-center">Search Results for Name</h4>
        <div class="name-contain w-100 d-flex ga-1 pa-2 mt-3">
          <div class="w-100 pa-2">
            <v-sheet>
              <v-form fast-fail @submit.prevent class="d-flex w-100 ga-2">
                <div class="form-field w-75">
                  <v-text-field v-model="resultName" label="Search Result For Name"></v-text-field>
                  <v-text-field v-model="resultPlace" label="Search Result For Place"></v-text-field>
                </div>
                <div class="field-btn w-25 d-flex justify-center align-end">
                  <v-btn class="bg-yellow mb-5" size="x-large" type="submit" @click="editResult_name" block>Edit</v-btn>
                </div>
              </v-form>
            </v-sheet>
          </div>
        </div>
      </div>


        <!-- Show only ID card search content -->
        <div v-if="showSearch" class="w-100 pa-2 search_c d-flex ga-2 flex-column justify-center align-center">
          <v-sheet class="mx-auto" width="300">
            <v-form @submit.prevent>
              <h3 class="text-center">Search for result ID</h3>
              <div class="editbox mt-3 d-flex ga-3 justify-center">
                <v-text-field v-model="searchResult" :label="'Search result for ' + selectedTag"></v-text-field>
                <v-btn size="x-large" class="bg-yellow" @click="editResult_id">Edit</v-btn>
              </div>
            </v-form>
          </v-sheet>
          
        </div>
     

      
      
    </v-card>
    </div>
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
      tab: 'tab-1',
    showSearch: false,
    showMainContent: true,
    showNameContain: false,
    showMobileContain:false,
    selectedTag: '',
    tags: [
      'Aadhaar',
      'VoterID',
      'Driving License',
      'Mnrega',
      'Bank Passbook',
      'Other',
    ],
    idnumber: '',
    rules: [
      value => !!value || 'Required.',
      value => (value && /^\d{4}$/.test(value)) || 'Must be 4 digits',
    ],
    name: '',
    place: '',
    mobile: '',
    resultName: '', // This will hold the search result for Name
    resultPlace: '', // This will hold the search result for Place
    searchResult: '', // This will hold the value to be displayed in search_c
    mobileResult:'',
   
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
    selectTag(tag) {
    this.selectedTag = tag;
  },
  toggleSearch() {
    if (this.selectedTag === 'Aadhaar' || this.selectedTag === 'VoterID' || this.selectedTag === 'Driving License'|| this.selectedTag === 'Mnrega'|| this.selectedTag === 'Bank Passbook'|| this.selectedTag === 'Other') {
      if (this.idnumber && /^\d{4}$/.test(this.idnumber)) {
        this.searchResult = this.idnumber; // Assigning idnumber to searchResult
        this.showSearch = true;
        this.showMainContent = false;
      } else {
        alert('Please enter a valid 4-digit ID number.');
      }
    } else {
      alert('Please select an ID type first.');
    }
  },
  editResult_id() {
    this.showSearch = false; // Hide search_c
    this.showMainContent = true; // Show main content
    this.tab = 'tab-3'; // Switch to the "ID" tab
  },
  namesearch() {
    if (this.name.length >= 3 && this.place.length >= 3) {
      this.resultName = this.name; // Assigning name to resultName
      this.resultPlace = this.place; // Assigning place to resultPlace
      this.showNameContain = true; // Display namecontain on successful search
      this.showMainContent = false; // Hide tabs and form in tab-2
    } else {
      alert('Please enter at least 3 characters for both Name and Place.');
    }
  },
  editResult_name() {
    this.showNameContain = false; // Hide namecontain class
    this.showMainContent = true; // Show tabs and form in tab-2
    this.tab = 'tab-2'; // Switch to the "Name" tab
  },
  phone_loan_search(){
    if (this.mobile.length >= 5){
        this.mobileResult=this.mobile;
        this.showMainContent=false;
        this.showMobileContain=true;
    }
    else{
      alert('please enter at least 5 characters for both phone and loan')
    }
  },
  editResult_mobile(){
    this.showMobileContain=false;
    this.showMainContent=true;
    this.tab = 'tab-1';
  }

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
</style>
x