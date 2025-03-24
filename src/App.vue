<script setup>

import UserReview from './components/UserReview.vue';
</script>

<template>
  <header>
    <h1>Heavy metal sentiment analyzer</h1>
    <img alt="mainImage" class="logo" src="./assets/mainImage.jpg" width="125" height="125" />
  </header>

  <main>
    <div class="wrapper">
      <UserReview></UserReview>
    </div>

  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

h1 {
  align-items: center;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
    padding-right: 100%;
    width: 100%;
    height: 25%;

  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    align-items: center;
    flex-wrap: wrap;

  }
}

</style>
