<script setup lang="ts">
import { nextTick, onMounted, reactive, Ref, ref } from "vue";
import Vidoejs from 'video.js/dist/video'
import 'videojs-flash'



defineProps<{ msg: string }>();

const count: Ref<number> = ref(0);
interface Man {
  name: string,
  age: number
}
const person: Man = reactive({
  name: '',
  age: 0,
});

onMounted(() => {
  nextTick(() => {
    const videoPlayer = new Vidoejs('#Video', {
      autoplay: 'muted',
      controls: true,
      aspectRatio: "16:9",
      techOrder: ['html5'],
      sources: [{ src:'http://kefuzhihua-1300902972.cos.ap-nanjing.myqcloud.com/1642488976180-c6883103-0bbc-4a0a-97b8-b598add8b943_material%20%281%29.mp4',type:'video/mp4'}]
    })
  })
})

</script>

<template>
  <div>
    <h1>{{  msg  }}</h1>

    <div class="card">
      <button type="button" @click="count++">count is {{  count  }}</button>
      <br>
      <button type="button" @click="person.name = 'xiaoming'">name is {{  person.name  }}</button>
      <p>
        Edit
        <code>components/HelloWorld.vue</code> to test HMR
      </p>
    </div>

    <p>
      Check out
      <a href="https://vuejs.org/guide/quick-start.html#local" target="_blank">create-vue</a>, the official Vue + Vite
      starter
    </p>
    <p>
      Install
      <a href="https://github.com/johnsoncodehk/volar" target="_blank">Volar</a>
      in your IDE for a better DX
    </p>
    <p class="read-the-docs">Click on the Vite and Vue logos to learn more</p>
  </div>
  <video id="Video"></video>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}

#Video {
  width: 400px;
  height: 225px;
  padding: 0px;
}
</style>
