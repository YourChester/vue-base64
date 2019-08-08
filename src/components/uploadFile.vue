<template>
  <v-layout align-center justify-center row fill-height>
    <v-flex md5 class="mr-3">
      <v-file-input
        label="File input"
        @change="getFileInBase64"
      ></v-file-input>
    </v-flex>
    <v-flex md1>
      <v-btn
        color="primary"
        depressed
        :disabled="ready"
        @click="saveToLocalStore"
      >
        Upload
        <v-icon
          small
        >
          cloud-upload
        </v-icon>
      </v-btn>
    </v-flex>
  </v-layout>
</template>

<script>
export default {
  name: 'upload-file',
  data: () => ({
    file: '',
    ready: true,
  }),
  methods: {
    getFileInBase64()  {
      const inputFile = document.querySelector('input[type="file"]').files[0]
      const reader = new FileReader()
      reader.readAsDataURL(inputFile)
      reader.onload = () => {
        this.file = reader.result
        this.ready = false
      };
      reader.onerror = (error) => {
        console.log('Error: ', error)
      };
    },
    saveToLocalStore() {
      const objToSave = {
        file: this.file,
      }
      localStorage.setItem('photo', JSON.stringify(objToSave))
    }
  }
}
</script>


