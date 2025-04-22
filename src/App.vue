<template>
  <nav>
    <img
      alt="GreenTechlogo"
      id="greentechlogo"
      src="@/assets/greentechlogo.png"
    />
  </nav>
  <router-view />
</template>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@400;500;700&display=swap");
@import url("https://fonts.googleapis.com/css2?family=ABeeZee&display=swap");

html,
body,
#app {
  min-height: 100dvh;
  background-color: #f4f2ee;
}

#greentechlogo {
  width: 122.83px;
  height: 40px;
  position: absolute;
  top: 30px;
  left: 35px;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.25s;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
