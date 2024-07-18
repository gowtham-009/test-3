<template>
  <div class="main-container w-100" :style="{height: deviceHeight + 'px'}">
    <div class="w-100 boxex-1":style="{height:boxex1Height + 'px'}">
      <logo/>
    </div>
    <div class="w-100 boxex-2 pa-2":style="{height:boxex2Height + 'px'}">
      <div class="loan-1 w-100  d-flex  ga-2" >
        <div class="w-100"><v-text-field label="SF-AA--" variant="solo"></v-text-field></div>
        <div class="w-100 d-flex justify-center"><p class="text-blue text-center text-h6 mt-2">New Loan</p></div>
        <div class="w-100"> <v-date-input label="00-00-0000" prepend-icon="" variant="solo"></v-date-input></div>
      </div>
      <div class="loan-2 w-100 d-flex  ga-10 justify-center align-center  " >
        <v-checkbox class="text-h6" style="height: 50px;" label="Gold"></v-checkbox>
        <v-checkbox class="text-h6" style="height: 50px;" label="Silver"></v-checkbox>
        <v-checkbox class="text-h6" style="height: 50px;" label="Brass"></v-checkbox>
      </div>

      <div class="loan-3 w-100" >
        <v-form v-model="valid">
          <v-container class="pa-0">
              <v-row no-gutters>
                <v-col cols="12">
                  <v-sheet class=" d-flex flex-column ga-4">
                    <v-text-field
                      v-model="loanvalue"
                      :counter="10"
                      :rules="loanRules"
                      label="Loan Value:"
                      placeholder="0.00"
                      hide-details
                      required
                      class="w-100"
                    ></v-text-field>
                    <v-text-field
                      v-model="loanhandover"
                      :counter="10"
                      :rules="loan_hand_overRules"
                      label="Loan Handover:"
                      placeholder="0.0"
                      hide-details
                      required
                      class="w-100"
                    ></v-text-field>
                    <v-text-field
                      v-model="weight"
                      :counter="10"
                      :rules="weightRules"
                      label="Weight:"
                      placeholder="000.000"
                      hide-details
                      required
                      class="w-100"
                    ></v-text-field>
                    <v-text-field
                      v-model="pawn"
                      :counter="10"
                      :rules="pawnRules"
                      label="Pawn_Details:"
                       placeholder="English / தமிழ்"
                      hide-details
                      required
                    ></v-text-field>
                  </v-sheet>
                </v-col>
                <v-col cols="12" class="d-flex">
                  <div class="w-50 d-flex">
                    <div class="w-100 d-flex flex-column pa-2">
                        <h5>Porul:</h5>
                        <div class="card pa-2 d-flex flex-column justify-center align-center ga-3 rounded-lg bg-grey-lighten-3 w-100">
                          <v-icon icon="mdi-file-upload" class="text-h4"></v-icon>
                          <p class="text-center">Drag and drop <br /> File Here</p>
                          <v-btn class="bg-red rounded-lg text-white" @click="showCamera('porul')">Capture Photo</v-btn>
                          <div class="w-100 pic rounded-lg">
                            <img v-if="photos.porul" :src="photos.porul" alt="porul Photo" class="captured-photo rounded-lg" />
                            <v-btn block v-if="photos.porul" class="edit-btn bg-yellow text-black mb-3" @click="showCamera('porul')">Edit</v-btn>
                          </div>
                        </div>
                      </div>

                  </div> 
                  <div class="w-50 d-flex">
                    <div class="w-100 d-flex flex-column pa-2">
                        <h5>Person:</h5>
                        <div class="card pa-2 d-flex flex-column justify-center align-center ga-3 rounded-lg bg-grey-lighten-3 w-100">
                      <v-icon icon="mdi-file-upload" class="text-h4"></v-icon>
                      <p class="text-center">Drag and drop <br /> File Here</p>
                      <v-btn class="bg-red rounded-lg text-white" @click="showCamera('person')">Capture Photo</v-btn>
                      <div class="w-100 pic rounded-lg">
                        <img v-if="photos.person" :src="photos.person" alt="Person Photo" class="captured-photo rounded-lg" />
                        <v-btn block v-if="photos.person" class="edit-btn bg-yellow text-black mb-3" @click="showCamera('person')">Edit</v-btn>
                      </div>
                    </div>
                      </div>

                  </div>
                </v-col>
              </v-row>

              <v-row no-gutters class="mt-2">
                <v-col>
                  
                </v-col>
              </v-row>  
            </v-container>
        </v-form>
      </div>
    </div>

    <div class="w-100 d-flex ga-2 pa-2 align-center" :style="{height:boxex3Height + 'px'}">
        <div class="w-100"><v-btn class="bg-yellow text-black" block>Reset</v-btn></div>
        <div class="w-100"><nuxt-link to="/loan_success" style="text-decoration: none;"><v-btn class="bg-green text-white" block>Proceed For Esign</v-btn></nuxt-link></div>
      </div>
  </div>

  <div v-if="showCameraOverlay" class="camera-overlay">
    <video ref="video" class="video w-100" autoplay></video>
    <div class="w-100 d-flex justify-center ga-2">
      <v-btn block class="capture-btn" @click="takePhoto">Take Photo</v-btn>
      <v-btn block class="close-btn bg-red text-white" @click="closeCamera">Cancel</v-btn>
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
      boxex3Height: 0,
      showCameraOverlay: false,
      currentPhotoType: '',
      videoStream: null,
      photos: {
        porul: '',
        person: ''
      },
      showCaptureButtons: true // Flag to toggle capture/edit mode
      

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
    async showCamera(photoType) {
      this.currentPhotoType = photoType;
      this.showCameraOverlay = true;
      try {
        this.videoStream = await navigator.mediaDevices.getUserMedia({ video: true });
        this.$refs.video.srcObject = this.videoStream;
      } catch (error) {
        console.error('Error accessing camera: ', error);
        this.showCameraOverlay = false;
      }
    },
    takePhoto() {
      const canvas = document.createElement('canvas');
      canvas.width = this.$refs.video.videoWidth;
      canvas.height = this.$refs.video.videoHeight;
      const context = canvas.getContext('2d');
      context.drawImage(this.$refs.video, 0, 0, canvas.width, canvas.height);
      const dataUrl = canvas.toDataURL('image/png');
      // Directly mutate the reactive property 'photos'
      this.photos[this.currentPhotoType] = dataUrl;
      this.closeCamera();
      this.showCaptureButtons = false; // Hide capture buttons after photo is taken
    },
    editPhoto(type) {
      this.currentPhotoType = type;
      this.showCameraOverlay = true;
      this.showCaptureButtons = true; // Show capture buttons again for editing
    },
    closeCamera() {
      this.showCameraOverlay = false;
      if (this.videoStream) {
        this.videoStream.getTracks().forEach(track => track.stop());
      }
      this.videoStream = null;
    }

  }
};
</script>

<style scoped>

.boxex-2{
  overflow: hidden;
  overflow: scroll;
}
.camera-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background-color: rgba(0, 0, 0, 0.8);
  display: flex;
  align-items: flex-start;
  justify-content: flex-start;
  flex-direction: column;
  z-index: 1000;
}
.video {
  width: 100%;
  object-fit: cover;
  height: 90%;
}
.capture-btn,
.close-btn {
  margin-top: 20px;
  background-color: white;
  color: black;
}
.captured-photo {
  width: 100%;
  object-fit: cover;
  height: 150px;
}
.edit-btn {
  margin-top: 10px;
}
.card{
  position: relative;
}
.pic {
  position:absolute;
  top: 0%;
}
</style>
