<template>
  <div class="container">
    <div class="notifications-container">
      <div class="notifications-header">
        <h3 class="notifications-title">Notifications</h3>
        <button @click="markAllAsRead">
          <span class="notifications-markAllAsRead">Mark all as read</span>
        </button>
      </div>
      <div class="notifications-cardsContainer">
        <Notification ref="Notification" />
        <Notification ref="Notification" />
      </div>
    </div>
  </div>
</template>

<script>
import Notification from './components/Notification.vue'

export default {
  name: 'App',
  components: { Notification },
  methods: {
    markAllAsRead() {
      this.$refs.Notification.toggleAlert()
    }
  }
}
</script>

<style lang="scss">

@import url(custom.scss);

.notifications-container {
  margin: 30px auto;
  padding: 30px 20px;
  max-width: 1110px;
  display: flex;
  flex-direction: column;
  align-self: center;
  align-items: center;
  background-color: white;
  border-radius: 15px;
}

.notifications-header {
  margin: 8px 30px;
  width: 90%;
  align-self: flex-start;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.notifications-cardsContainer {
  margin: 8px 30px;
  width: 90%;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.notifications-title {
  font-size: 24px;
  line-height: 30px;
  font-weight: 800;
  color: #1C202B;
}

.notifications-markAllAsRead {
  font-size: 16px;
  line-height: 20px;
  font-weight: 500;
  color: #5E6778;
  transition: all ease-in-out 0.4s;

  &:hover {
    color: #0A327B;
  }
}

</style>
