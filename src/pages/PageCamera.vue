<template>
  <q-page class="constrain-more q-pa-md">
    <div class="camera-frame q-pa-md">

      
      <video
        v-show="!imageCaptured"
        ref="video"
        class="full-width"
        autoplay></video>
      
      <canvas
        v-show="imageCaptured"
        ref="canvas"
        class="full-width"
        height="240"></canvas>
      
    </div>
    <div class="text-center q-pa-md">
      <q-btn
        v-if="hasCameraSupport"
        @click="captureImage"
        round
        color="primary"
        icon="eva-camera" 
        size="lg"
      />
      
      <q-file
        v-if="!hasCameraSupport"
        outlined
        v-model="imageUpload"
        @input="captureImageFallback"
        label="Chose an image"
        accept="image/*"
      >
        <template v-slot:prepend>
          <q-icon name="eva-attach-outline" />
        </template>
      </q-file>

    </div>
    <div class="row justify-center q-ma-md">
      <q-input
        v-model="post.caption"        
        label="Caption"
        class="col col-sm-6"
        dense
      />
    </div>
    <div class="row justify-center q-ma-md">
      <q-input
        v-model="post.location"
        label="Location"
        class="col col-sm-6"
        dense
      >
        <template v-slot:append>
          <q-btn round dense flat icon="place" />
        </template>
      </q-input>
    </div>
    <div class="row justify-center q-mt-lg">
      <q-btn unelevated rounded color="primary" label="Post Image" />
    </div>
  </q-page>
</template>

<script>
import { uid } from 'quasar'
export default {
  name: 'PageCamera',
  data() {
    return {
      post: {
        id: uid(),
        caption: '',
        location: '',
        photo: null,
        date: Date.now()
      },
      imageCaptured: false,
      imageUpload: [],
      hasCameraSupport: true
    }
  },
  methods: {
    initCamera () {
      navigator.mediaDevices.getUserMedia({
        video: true
      }).then(stream => {
        this.$refs.video.srcObject = stream
      }).catch(error => {
        this.hasCameraSupport = false
      })
    },
      captureImage (){
        let video = this.$refs.video
        let canvas = this.$refs.canvas
        canvas.width = video.getBoundingClientRect().width
        canvas.height = video.getBoundingClientRect().height
        let context = canvas.getContext('2d')
        context.drawImage(video, 0, 0, canvas.width, canvas.height)
        this.imageCaptured = true
        this.post.photo = this.dataURItoBlob(canvas.toDataURL())
        this.disableCamera()
    },
      captureImageFallback(file){
        this.post.photo = file
  
        let canvas = this.$refs.canvas
        let context = canvas.getContext('2d')

        var reader = new FileReader()
        reader.onload = event => {
          var img = new Image()
          img.onload = () => {
            canvas.width = img.width
            canvas.height = img.height
            context.drawImage(img,0,0)
            this.imageCaptured = true
          }
          img.src = event.target.result
        }
        reader.readAsDataURL(file)
      },

      disableCamera(){
        this.$refs.video.srcObject.getVideoTracks().forEach(track => {
          track.stop()
        })
      },
  
      dataURItoBlob(dataURI) {
        var byteString = atob(dataURI.split(',')[1]);
        var mimeString = dataURI.split(',')[0].split(':')[1].split(';')[0]
        var ab = new ArrayBuffer(byteString.length);
        var ia = new Uint8Array(ab);
        for (var i = 0; i < byteString.length; i++) {
            ia[i] = byteString.charCodeAt(i);
        }
        var blob = new Blob([ab], {type: mimeString});
        return blob;
      }
  },
  mounted() {
    this.initCamera()
  },
  beforeDestroy () {
    if (this.hasCameraSupport) {
      this.disableCamera()    
    }
  }
}
</script>

<style lang="sass">
  .camera-frame
    border: 2px solid $grey-10
    border-radius: 10px
</style>


