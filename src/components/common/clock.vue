<template>
  <div class="clock">
    <span>{{time}}</span>
  </div>
</template>

<script>
import { ref, onMounted, onUnmounted } from 'vue';
import dayjs from 'dayjs';

export default {
  setup() {
    const time = ref('');
    let timer = null;
    // events
    onMounted(() => {
      timer = setInterval(() => {
        time.value = dayjs().format('HH:mm');
      });
    });
    onUnmounted(() => {
      clearInterval(timer);
      timer = null;
    });
    return {
      time,
    };
  },
};
</script>
