<template lang="pug">
      <div class="html-clock">
        <div class="hours">{{ hours }}</div>
        <div class="sep">:</div>
        <div class="minutes">{{ minutes }}</div>
        <div class="sep">:</div>
        <div class="seconds">{{ seconds }}</div>
        <div class="format">{{ format }}</div>
    </div>
</template>
    
<script lang="ts">
import Vue from "vue";
export default Vue.extend({
  props: ["theme"],
  data() {
    return {
      hours: "--",
      minutes: "--",
      seconds: "--",
      format: "--"
    };
  },
  methods: {
    updateCurrentTime() {
      const date = new Date();
      this.hours = date
        .getHours()
        .toString()
        .padStart(2, "0");
      this.minutes = date
        .getMinutes()
        .toString()
        .padStart(2, "0");
      this.seconds = date
        .getSeconds()
        .toString()
        .padStart(2, "0");
      this.format = this.hours >= 12 ? "PM" : "AM";
    },
    start() {
      setInterval(this.updateCurrentTime, 1000);
    }
  },
  mounted() {
    document.title = "VueClock.js";
    this.start();
  }
});
</script>

<style lang="postcss" scoped>
.html-clock {
  display: grid;
  grid-template-columns: 3fr 1fr 3fr 1fr 3fr 1.5fr;
  justify-content: center;
  align-items: center;
  width: 500px;
  height: 125px;
}

.html-clock > div {
  display: flex;
  justify-content: center;
}

.sep {
  animation: blink 1s linear infinite;
}

@keyframes blink {
  0%,
  49% {
    opacity: 1;
  }

  50%,
  100% {
    opacity: 0;
  }
}

.red-lcd {
  color: red;
}

.green-lcd {
  color: green;
}

.yellow-lcd {
  color: yellow;
}
</style>
