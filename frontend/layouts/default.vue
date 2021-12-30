<template>
  <div class='main-container'>
    <el-container direction='vertical'>
      <HomeMainHeader />
      <el-main>
        <div class='main-body'>
          <Nuxt />
        </div>
      </el-main>
      <HomeMainFooter />
    </el-container>
  </div>
</template>

<script>

export default {
  async asyncData({ store, route }) {
  }
};

</script>

<style scoped lang='scss'>
.main-container {
  @apply sm:px-0;
  @apply md:px-14;
  @apply lg:px-8;
  @apply xl:px-24;
  @apply 2xl:px-28;
}

.main-body {
  @apply px-6;
  @apply h-full;
}
</style>
