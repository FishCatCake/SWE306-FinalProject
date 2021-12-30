<template>
  <div>
    <CustomPageTitle>Room List</CustomPageTitle>
    <div class='room-card-wrapper'>
      <div v-for='item in rooms' :key='item.id' class='room-card-item'>
        <RoomCard :room='item' />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  middleware: ['auth'],
  async asyncData({ store }) {
    await store.dispatch('room/fetchRoomList');
    return { rooms: store.getters['room/roomList'] };
  },
  data() {
    return {
      rooms: []
    };
  },
  head() {
    return {
      title: 'XMUM Room Reservation',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'Available rooms for reservation'
        }
      ]
    };
  },

  methods: {}
};
</script>

<style scoped lang='scss'>
.room-card-wrapper {
  @apply flex flex-wrap flex-row justify-center;
}

.room-card-item {
  @apply mb-1.5;
  @apply w-full;

  @apply md:mb-3.5;
  @apply md:w-full;

  @apply lg:w-72;
  @apply lg:mr-3.5;

  @apply xl:mb-6;
  @apply xl:mr-6;
  @apply xl:w-96;

}
</style>
