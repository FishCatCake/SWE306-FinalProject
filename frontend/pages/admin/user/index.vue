<template>
  <div>
    <CustomPageTitle>User Management</CustomPageTitle>
    <div class='options'>
      <el-button @click='handleAddUser' type='primary'>Add User</el-button>
    </div>
    <el-table :data='userList' stripe height='800'>
      <el-table-column
        type='index'
        fixed
        width='50'>
      </el-table-column>
      <el-table-column
        prop='username'
        label='Username'
        sortable
        fixed
        fit
      >
      </el-table-column>
      <el-table-column
        prop='firstName'
        fit
        sortable
        label='First Name'
      >
      </el-table-column>
      <el-table-column
        prop='lastName'
        fit
        sortable
        label='Last Name'
      >
      </el-table-column>
      <el-table-column
        prop='phoneNum'
        label='Tel.'
        sortable
        width='200'>
      </el-table-column>

      <el-table-column
        label='Role'
        width='100'>
        <template slot-scope='scope'>
          <div slot='reference' class='name-wrapper'>
            <el-tag v-if='scope.row.isAdmin' type='info' size='small'>Admin</el-tag>
            <el-tag v-else type='primary' size='small'>Student</el-tag>
          </div>
        </template>
      </el-table-column>
      <el-table-column label='Action' fixed='right' width='200'>
        <template slot-scope='scope'>
          <el-button
            size='mini'
            @click='handleEdit(scope.$index, scope.row)'>Edit
          </el-button>
          <el-button
            size='mini'
            type='danger'
            @click='handleDelete(scope.$index, scope.row)'>Delete
          </el-button>
        </template>
      </el-table-column>
    </el-table>
  </div>
</template>

<script>
import Element from 'element-ui';

export default {
  name: 'user management',
  middleware: ['adminAuth'],
  async asyncData({ app }) {
    const resp = await app.$api.$get('/getUserAll');
    let userList = [];
    if (resp.success) {
      userList = resp.content;
    } else {
      app.$message.error(resp.message);
    }
    return {
      userList
    };
  },
  data() {
    return {
      userList: []
    };
  },
  methods: {
    handleEdit(index, row) {
      // console.log(row.userId);
      this.$router.push('/admin/user/' + row.userId);
    },
    handleAddUser() {
      this.$router.push('/admin/user/add');
    },
    handleDelete(index, row) {
      Element.MessageBox.alert(
        'You cannot delete user in demo mode',
        'Warning',
        {
          type: 'warning'
        });
    }

  }
};
</script>

<style scoped lang='scss'>
.options {
  @apply flex justify-end;
}
</style>
