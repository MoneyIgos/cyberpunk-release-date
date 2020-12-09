<template>
  <v-app dark>
    <v-main dark class="accent--text">
      <v-container>
        <v-img
          src="https://assets.rpgsite.net/images/images/000/067/600/original/Cyberpunk-2077_logo.png"
          max-height="300"
        ></v-img>
        <b>Premiera za:</b>
        <p v-if="timeToRelease < 0" class="text-h3">
          <b>Wake the fuck up, samurai! We have a city to burn.</b>
        </p>
        <p v-else class="text-h3">
          {{ HowLongToReleaseDay }} Dni, {{ HowLongToReleaseHour }} Godzin,
          {{ HowLongToReleaseMinute }} Minut,
          {{ HowLongToReleaseSecond }} Sekund
        </p>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      HowLongToReleaseDay: 0,
      HowLongToReleaseHour: 0,
      HowLongToReleaseMinute: 0,
      HowLongToReleaseSecond: 0,
      timeToRelease: 1,
    };
  },
  mounted() {
    const cpRelease = new Date('Dec 10, 2020 01:00:00').getTime();

    setInterval(() => {
      const timeNow = new Date().getTime();
      const timeToRelease = cpRelease - timeNow;
      this.timeToRelease = timeToRelease;

      this.HowLongToReleaseDay = Math.floor(
        timeToRelease / (1000 * 60 * 60 * 24)
      );
      this.HowLongToReleaseHour = Math.floor(
        (timeToRelease % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60)
      );
      this.HowLongToReleaseMinute = Math.floor(
        (timeToRelease % (1000 * 60 * 60)) / (1000 * 60)
      );
      this.HowLongToReleaseSecond = Math.floor(
        (timeToRelease % (1000 * 60)) / 1000
      );
    }, 1000);
  },
};
</script>
