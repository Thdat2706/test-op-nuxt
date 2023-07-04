<template>
  <div>
    <button v-if="!isRecording" @click="startRecording">Start Recording</button>
    <button v-else @click="stopRecording">Stop Recording</button>
  </div>
</template>

<script>
export default {
  layout: 'navbarAddBack',
  data() {
    return {
      isRecording: false,
      mediaRecorder: null,
      recordedChunks: [],
    }
  },
  methods: {
    async startRecording() {
      const stream = await navigator.mediaDevices.getUserMedia({ audio: true })

      this.recordedChunks = []

      this.mediaRecorder = new MediaRecorder(stream)

      this.mediaRecorder.addEventListener('dataavailable', (event) => {
        if (event.data.size > 0) {
          console.log(event.data)
          this.recordedChunks.push(event.data)
        }
      })

      this.mediaRecorder.addEventListener('stop', () => {
        const audioBlob = new Blob(this.recordedChunks, { type: 'audio/webm' })
        const audioUrl = URL.createObjectURL(audioBlob) // put object to s3 service here

        // Do something with the recorded audio, e.g., save it to a server, play it, etc.
        console.log('Recorded audio URL:', audioUrl)

        this.isRecording = false
      })

      this.mediaRecorder.start()
      this.isRecording = true
      // .catch((error) => {
      //   console.log('Error accessing microphone:', error)
      // })
    },
    stopRecording() {
      this.mediaRecorder.stop()
    },
  },
}
</script>

<style scope></style>
