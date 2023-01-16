<template>
  <div class="container">
    <div class="notifications-container">
      <div class="notifications-header">
        <div class="notifications-headerTitle">
          <h3 class="notifications-title">Notifications</h3>
          <span class="notifications-number">5</span>
        </div>
        <button @click="markAllAsRead">
          <span class="notifications-markAllAsRead">Mark all as read</span>
        </button>
      </div>
      <div class="notifications-cardsContainer">
        <Notification :picture-filename="require('../src/assets/notifications-page-main/assets/images/avatar-mark-webber.webp')" :name="'Mark Weber'" :default-text="'reacted to your recent post'" :post="'My first tournament today!'" :time="'1m ago'" ref="Notification" />
        <Notification :picture-filename="require('../src/assets/notifications-page-main/assets/images/avatar-angela-gray.webp')" :name="'Angela Gray'" :default-text="'followed you'" :post="''" :time="'1m ago'" ref="Notification" />
        <Notification :picture-filename="require('../src/assets/notifications-page-main/assets/images/avatar-jacob-thompson.webp')" :name="'Jacob Thompson'" :default-text="'has joined your group'" :post="''" :group="'Chess Club'" :time="'1 day ago'" ref="Notification" />
        <Notification :picture-filename="require('../src/assets/notifications-page-main/assets/images/avatar-rizky-hasanuddin.webp')" :name="'Rizky Hasanuddin'" :default-text="'sent you a private message'" :post="''" :group="''" :time="'5 days ago'" :message="'Hello, thanks for setting up the Chess Club. I’ve been a member for a few weeks now and I’m already having lots of fun and improving my game.'" ref="Notification" />
        <Notification :picture-filename="require('../src/assets/notifications-page-main/assets/images/avatar-kimberly-smith.webp')" :name="'Kimberly Smith'" :default-text="'commented on your picture'" :post="''" :group="''" :time="'1 week ago'" ref="Notification" />
        <Notification :picture-filename="require('../src/assets/notifications-page-main/assets/images/avatar-nathan-peterson.webp')" :name="'Nathan Peterson'" :default-text="'reacted to your recent post'" :post="'5 end-game strategies to increase your win rate'" :group="''" :time="'2 weeks ago'" ref="Notification" />
        <Notification :picture-filename="require('../src/assets/notifications-page-main/assets/images/avatar-anna-kim.webp')" :name="'Anna Kim'" :default-text="'left the group'" :post="''" :group="'Chess Club'" :time="'2 weeks ago'" ref="Notification" />
      </div>
    </div>
  </div>
</template>

<script>
import Notification from './components/Notification.vue'

export default {
  name: 'App',
  components: { Notification },
  data() {
    return {
      notifNumbers: null
    }
  },
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
  max-width: 900px;
  display: flex;
  flex-direction: column;
  align-self: center;
  align-items: center;
  background-color: white;
  border-radius: 15px;
  box-shadow: 0px 20px 60px rgba(73, 97, 168, 0.05);
}

.notifications-header {
  margin: 8px 30px;
  width: 90%;
  align-self: flex-start;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.notifications-headerTitle {
  display: flex;
  align-items: center;
  gap: 10px;
}

.notifications-number {
  padding: 5px 15px;
  font-size: 16px;
  line-height: 20px;
  font-weight: 800;
  border-radius: 6px;
  color: white;
  background-color: #0A327B;
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
