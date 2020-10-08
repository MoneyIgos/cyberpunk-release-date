<template>
  <div class="home">
    <h1>Cyberpunk</h1>
    <p>{{ HowLongToRelease }}</p>
  </div>
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

      this.HowLongToRelease = `Premiera za:
       ${timeToRelease.getMonth() - 1} Miesiąc,
       ${timeToRelease.getDate()} Dni,
       ${timeToRelease.getHours()} Godzin,
       ${timeToRelease.getMinutes()} Minut i
       ${timeToRelease.getSeconds()} Sekund`;
    }, 100);
  },
};
</script>
