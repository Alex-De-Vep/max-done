<template>
  <router-view />
</template>

<style>
:root {
  /*Fonts*/
  --font-stack: "Montserrat", Arial, sans-serif;

  /*Colors*/
  --text: #394f61;
  --light-text: #7085a5;
}

body,
h1,
p {
  margin: 0;
}

body {
  font-family: var(--font-stack);
}

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
