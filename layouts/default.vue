<template>
  <div>
    <Header />
    <div class="c-main">
        <Sidebar />
        <div class="c-content">
            <Nuxt />
        </div>
    </div>
    <Footer />
  </div>
</template>


<style scoped>
  .c-main {
      display: flex;
  }
  @media screen and (max-width: 768px) {
    .c-main {
      flex-direction: column;
    }
    }
  .c-content {
      flex: 1;
  }
</style>