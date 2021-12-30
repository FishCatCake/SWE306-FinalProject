<template>
  <div>
    <CustomPageTitle>Add New User</CustomPageTitle>
    <div class='mb-5'>
      <el-alert
        type='warning'
        title='Demo Mode'
        show-icon>
        You cannot add new user in demo mode.
      </el-alert>
    </div>
    <UserEditor method='add' disabled />

  </div>
</template>

<script>
export default {
  name: 'add user',
  middleware: ['adminAuth']

};
</script>

<style scoped>

</style>
