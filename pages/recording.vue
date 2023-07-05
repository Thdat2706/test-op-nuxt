<template>
  <div>
    <button v-if="!isRecording" @click="startRecording">Start Recording</button>
    <button v-else @click="stopRecording">Stop Recording</button>
    <section class="sound-clips"></section>
  </div>
</template>

<script>
export default {
  layout: "navbarAddBack",
  data() {
    return {
      isRecording: false,
      mediaRecorder: null,
      recordedChunks: [],
    };
  },
  methods: {
    async startRecording() {
      const stream = await navigator.mediaDevices.getUserMedia({ audio: true });

      this.recordedChunks = [];

      this.mediaRecorder = new MediaRecorder(stream);

      this.mediaRecorder.addEventListener("dataavailable", (event) => {
        if (event.data.size > 0) {
          console.log(event.data);
          this.recordedChunks.push(event.data);
        }
      });

      this.mediaRecorder.addEventListener("stop", () => {
        const soundClips = document.querySelector(".sound-clips");

        const clipContainer = document.createElement("article");
        const clipLabel = document.createElement("p");
        const audio = document.createElement("audio");
        const deleteButton = document.createElement("button");

        clipContainer.classList.add("clip");
        audio.setAttribute("controls", "");
        deleteButton.textContent = "Delete";
        deleteButton.className = "delete";

        const audioBlob = new Blob(this.recordedChunks, { type: "audio/webm" });
        const audioUrl = URL.createObjectURL(audioBlob); // put object to s3 service here

        audio.controls = true;
        audio.src = audioUrl;
        // Do something with the recorded audio, e.g., save it to a server, play it, etc.
        console.log("Recorded audio URL:", audioUrl);

        this.isRecording = false;

        const clipName = prompt(
          "Enter a name for your sound clip?",
          "My unnamed clip"
        );

        if (clipName === null) {
          clipLabel.textContent = "My unnamed clip";
        } else {
          clipLabel.textContent = clipName;
        }

        clipContainer.appendChild(clipLabel);
        clipContainer.appendChild(audio);
        clipContainer.appendChild(deleteButton);
        soundClips.appendChild(clipContainer);

        // const blob = new Blob(chunks, { type: "audio/ogg; codecs=opus" });
        // chunks = [];
        // const audioURL = window.URL.createObjectURL(blob);
        console.log("recorder stopped");

        deleteButton.onclick = function (e) {
          e.target.closest(".clip").remove();
        };

        clipLabel.onclick = function () {
          const existingName = clipLabel.textContent;
          const newClipName = prompt("Enter a new name for your sound clip?");
          if (newClipName === null) {
            clipLabel.textContent = existingName;
          } else {
            clipLabel.textContent = newClipName;
          }
        };
      });

      this.mediaRecorder.start();
      this.isRecording = true;
      // .catch((error) => {
      //   console.log('Error accessing microphone:', error)
      // })
    },
    stopRecording() {
      this.mediaRecorder.stop();
    },
  },
};
</script>

<style scope></style>
