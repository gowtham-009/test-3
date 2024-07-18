<template>
  <div class="main-container w-100" :style="{ height: deviceHeight + 'px' }">
    <div class="w-100 boxex-1" :style="{ height: boxex1Height + 'px' }">
      <logo />
    </div>
    <div class="w-100 boxex-2 pa-2" :style="{ height: boxex2Height + 'px' }">
      <div class="loan-3 w-100">
        <v-form v-model="valid">
          <v-container class="pa-0">
            <v-row no-gutters>
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
                        <v-btn v-if="photos.porul" class="edit-btn" @click="showCamera('porul')">Edit</v-btn>
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
                        <v-btn v-if="photos.person" class="edit-btn" @click="showCamera('person')">Edit</v-btn>
                      </div>
                    </div>
                  </div>
                </div>
              </v-col>
            </v-row>
            <v-row no-gutters class="mt-2">
              <v-col></v-col>
            </v-row>
          </v-container>
        </v-form>
      </div>
    </div>
    <div class="w-100 d-flex ga-2 pa-2 align-center" :style="{ height: boxex3Height + 'px' }">
      <div class="w-100">
        <v-btn class="bg-yellow text-black" block>Reset</v-btn>
      </div>
      <div class="w-100">
        <nuxt-link to="/loan_success" style="text-decoration: none;">
          <v-btn class="bg-green text-white" block>Proceed For Esign</v-btn>
        </nuxt-link>
      </div>
    </div>
  </div>

  <div v-if="showCameraOverlay" class="camera-overlay">
      <video ref="video" class="video w-100" autoplay></video>
      <div class="w-100 d-flex justify-center ga-2">
        <!-- Toggle between back and front camera -->
        <v-btn class="capture-btn" @click="switchCamera('environment')">Back Camera</v-btn>
        <v-btn class="capture-btn" @click="switchCamera('user')">Front Camera</v-btn>
        <v-btn class="capture-btn" @click="takePhoto">Take Photo</v-btn>
        <v-btn class="close-btn bg-red text-white" @click="closeCamera">Cancel</v-btn>
      </div>
    </div>
</template>

<script>
import logo from "~/components/logo.vue"
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
    this.updateDeviceDimensions();
    window.addEventListener('resize', this.updateDeviceDimensions);
  },
  beforeUnmount() { // Use beforeUnmount in Vue 3 instead of beforeDestroy
    window.removeEventListener('resize', this.updateDeviceDimensions);
    this.closeCamera();
  },
  methods: {
    updateDeviceDimensions() {
      this.deviceWidth = window.innerWidth;
      this.deviceHeight = window.innerHeight;
      this.boxex1Height = Math.floor(this.deviceHeight * 0.10);
      this.boxex2Height = Math.floor(this.deviceHeight * 0.85);
      this.boxex3Height = Math.floor(this.deviceHeight * 0.05);
    },
    async showCamera(photoType) {
      this.currentPhotoType = photoType;
      this.showCameraOverlay = true;
      try {
        const facingMode = this.currentPhotoType === 'porul' ? 'environment' : 'user';
        this.videoStream = await navigator.mediaDevices.getUserMedia({ video: { facingMode } });
        this.$refs.video.srcObject = this.videoStream;
      } catch (error) {
        console.error('Error accessing camera: ', error);
        this.showCameraOverlay = false;
      }
    },
    switchCamera(facingMode) {
      this.closeCamera();
      this.showCameraOverlay = true;
      this.currentPhotoType = facingMode === 'environment' ? 'porul' : 'person';
      this.showCamera(this.currentPhotoType);
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
.boxex-2 {
  overflow: hidden;
  overflow-y: scroll;
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
  height: 50%;
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
