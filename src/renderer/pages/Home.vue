<template>
  <div>
    <div>Home.vue</div>
    <button
      v-text="'Open Video'" 
      @click="test()"
    />
    <video 
      ref="player" 
      :src="videoPath" 
      type='video/mp4' 
      @click="toggle"
      controls
    />
  </div>
</template>

<script>
const { dialog } = require('electron').remote

// const videoPath = 'C:\\Users\\Matt\\Desktop\\Knives Out (2019).mp4'

export default {
  name: 'home',
  components: {},
  props: {},
  data () {
    return {
      videoPath: null
    }
  },
  computed: {
  },
  methods: {
    toggle: function () {
      let player = this.$refs.player
      if (player.paused) {
        player.play()
      } else {
        player.pause()
      }
    },
    test: function () {
      let openPath = dialog.showOpenDialog({
        title: 'Choose a video',
        properties: ['openFile'],
        filters: [
          { name: 'Videos', extensions: ['mkv', 'avi', 'mp4'] }
        ]
      })
      if (openPath) {
        this.videoPath = openPath
      }
    }
  },
  watch: {
  },
  created () {
  },
  mounted () {
  },
  updated () {
  },
  destroyed () {
  }
}
</script>

<style>
</style>
