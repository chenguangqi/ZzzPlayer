<!-- src/components/VideoPlayerInput.vue -->
<template>
  <div class="video-player-input">
    <input v-model="url" placeholder="Enter a video URL here" />
    <button @click="playVideo">Play</button>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
// import type { PlayInfo } from "../types";


const emit = defineEmits(["update"]);
const url = ref(""); // 使用 ref 来创建响应式变量

const handleInput = () => {
  console.log("Current URL:", url.value);
};

const playVideo = () => {
  // console.log(1, url.value)
  const indexUrl = url.value.replace("preview.m3u8", "index.m3u8");
  // console.log(2, indexUrl);
  // console.log(3, url.value);
  const newPlayInfo = {
    VideoId: 0,
    Source: indexUrl, // 使用输入框的内容 "https://test-streams.mux.dev/x36xhzz/x36xhzz.m3u8",
    CoverURL: "",
    Title: "视频介绍",
    Duration: "04:22",
    Description: "",
  }
  emit("update", newPlayInfo);
};
</script>

<style scoped>
.video-player-input {
  margin: 8px 0;
  display: flex;
}
input {
  width: 100%;
  padding: 10px;
}
button {
  margin-left: 5px;
  padding: 10px 20px;
}
</style>
