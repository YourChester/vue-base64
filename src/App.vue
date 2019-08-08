<template>
  <v-app>
    <v-content>
      <form-file/>
      <v-btn
        color="primary"
        depressed
        @click="viewImage"
      >
        View Photo
      </v-btn>
      <div ref="photo"></div>
    </v-content>
  </v-app>
</template>

<script>
import FormFile from '@/views/formFile.vue'

export default {
  name: 'App',
  components: {
    FormFile
  },
  data: () => ({
  }),
  methods: {
    viewImage() {
      const img = new Image()
      const fileObj = JSON.parse(localStorage.getItem('photo'))
      if (fileObj) {
        img.src = fileObj.file
        this.$refs.photo.appendChild(img)
      }
    }
  }
};
</script>
