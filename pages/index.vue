<template>
  <v-app dark>
    <v-main dark class="accent--text">
      <v-container>
        <v-img
          src="https://assets.rpgsite.net/images/images/000/067/600/original/Cyberpunk-2077_logo.png"
          max-height="300"
        ></v-img>
        <b>Premiera za:</b>
        <p class="text-h3">{{ HowLongToRelease }}</p>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      HowLongToRelease: 0,
    };
  },
  mounted() {
    const cpRelease = new Date(2020, 11, 19, 0, 0, 0);

    setInterval(() => {
      const timeNow = new Date();
      const timeToRelease = new Date(cpRelease - timeNow);

      if (
        timeToRelease.getMonth() - 1 === 0 &&
        timeToRelease.getDay() + 5 === 0 &&
        timeToRelease.getHours() - 2 === 0 &&
        timeToRelease.getMinutes() === 0 &&
        timeToRelease.getSeconds() + 1 === 0
      )
        this.HowLongToRelease = 'TERAZ';

      this.HowLongToRelease = `
       ${timeToRelease.getMonth() - 1} Miesiąc,
       ${timeToRelease.getDay() + 5} Dni,
       ${timeToRelease.getHours() - 2} Godzin,
       ${timeToRelease.getMinutes()} Minut i
       ${timeToRelease.getSeconds() + 1} Sekund`;
    }, 100);
  },
};
</script>
