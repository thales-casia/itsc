<template>
  <div>
    <canvas ref="canvas" width="500" height="500" style="width:100%"></canvas>
  </div>
</template>
<script setup lang="ts">
import { usePlatform } from '@/store';
import { computed, onMounted, ref, watch } from 'vue';
import { Platform } from '@/utils/platform'
const props = defineProps({
  id: String
})
const store = usePlatform();
const canvas = ref<HTMLCanvasElement>();
let platform:any;

watch(() => props.id, (val, old) => {
  console.log(val, old);

}, {immediate:true});

onMounted(() => {
  if(canvas.value) {
    platform = new Platform(canvas.value);
    platform.start();
  }
})
</script>
