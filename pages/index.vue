<template>
  <v-app dark>
    <v-content dark class="primary--text">
      <v-container>
        <v-img
          src="https://assets.rpgsite.net/images/images/000/067/600/original/Cyberpunk-2077_logo.png"
          max-height="300"
        ></v-img>
        <b>Premiera za:</b>
        <p class=".display-3">{{ HowLongToRelease }}</p>
      </v-container>
    </v-content>
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

      this.HowLongToRelease = `
       ${timeToRelease.getMonth() - 1} Miesiąc,
       ${timeToRelease.getDate()} Dni,
       ${timeToRelease.getHours()} Godzin,
       ${timeToRelease.getMinutes()} Minut i
       ${timeToRelease.getSeconds()} Sekund`;
    }, 100);
  },
};
</script>
