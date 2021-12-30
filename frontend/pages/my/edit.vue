<template>
  <div>
    <CustomPageTitle>Edit My Profile</CustomPageTitle>
    <div class='mb-5'>
      <el-alert
        type='warning'
        title='Demo Mode'
        show-icon>
        You cannot edit username and password in demo mode.
      </el-alert>
    </div>
    <UserEditor method='profile' :user-id='userId'></UserEditor>
  </div>
</template>

<script>
import { mapGetters } from 'vuex';

export default {
  name: 'edit user info',
  computed: {
    userId() {
      return this.loggedInUser.id;
    },
    ...mapGetters(['loggedInUser'])
  }
};
</script>

<style scoped lang='scss'>

</style>
