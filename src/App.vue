<template>
  <div class="container">
    <header>
      <div class="title">
        <h1>Notifications</h1>
        <span class="badge">{{ unreadNotificationCount }}</span>
      </div>
      <button id="markAll" @click="markAllUnread">Mark all as read</button>
    </header>
    <div class="wrapper">
      <div v-for="n in notifications" :key="n.id" @click="handleNotificationClick(n.id)" class="notification" :class="{ 'unread': n.isUnread }">
        <div class="notification-content">
            <img :src="n.author.src" :alt="n.author.name" class="headshot"/>
            <div class="post">
              <div>
                <div>
                  <div>
                    <a :href="n.author.href">
                      {{ n.author.name }}
                    </a>
                    <span> {{ n.text }}</span>
                    <a v-if="n.link" :href="n.link.href"> {{ n.link.text }}</a>
                    <span v-if="n.isUnread" class="isUnread"></span>
                  </div>
                </div>
                <p class="time">{{ n.time }}</p>
              </div>
              <p v-if="n.privateMessage" class="privateMessage">{{ n.privateMessage }}</p>
            </div>
          </div>
          <a v-if="n.image" :href="n.image.href">
            <img :src="n.image.src" :alt="n.image.alt" />
          </a>
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
      notifications: [
        {
          "id": "1",
          "author": {
            "name": "Mark Webber",
            "img": "./assets/notifications-page-main/assets/images/avatar-mark-webber.webp",
            "href": "#"
          },
          "text": "reacted to your recent post",
          "link": {
            "text": "My first tournament today!",
            "href": "#"
          },
          "time": "1m ago",
          "hasBeenRead": false,
        },
        {
          "id": "2",
          "author": {
            "name": "Angela Gray",
            "img": "./assets/notifications-page-main/assets/images/avatar-angela-gray.webp",
            "href": "#"
          },
          "text": "followed you",
          "link": {
            "text": "",
            "href": "#"
          },
          "time": "5m ago",
          "hasBeenRead": false,
        },
        {
          "id": "3",
          "author": {
            "name": "Jacob Thompson",
            "img": "./assets/notifications-page-main/assets/images/avatar-jacob-thompson.webp",
            "href": "#"
          },
          "text": "has joined your group",
          "link": {
            "text": "Chess Club",
            "href": "#"
          },
          "time": "1 day ago",
          "hasBeenRead": false,
        },
        {
          "id": "4",
          "author": {
            "name": "Rizky Hasanuddin",
            "img": "./assets/notifications-page-main/assets/images/avatar-rizky-hasanuddin.webp",
            "href": "#"
          },
          "text": "sent you a private message",
          "link": {
            "text": "",
            "href": "#"
          },
          "time": "5 days ago",
          "hasBeenRead": false,
        },
        {
          "id": "5",
          "author": {
            "name": "Kimberly Smith",
            "img": "./assets/notifications-page-main/assets/images/avatar-kimberly-smith.webp",
            "href": "#"
          },
          "text": "commented on your picture",
          "link": {
            "text": "",
            "href": "#"
          },
          "time": "1 week ago",
          "hasBeenRead": false,
        },
        {
          "id": "6",
          "author": {
            "name": "Nathan Peterson",
            "img": "./assets/notifications-page-main/assets/images/avatar-nathan-peterson.webp",
            "href": "#"
          },
          "text": "reacted to your recent post",
          "link": {
            "text": "5 end-game strategies to increase your win rate",
            "href": "#"
          },
          "time": "2 weeks ago",
          "hasBeenRead": false,
        },
        {
          "id": "7",
          "author": {
            "name": "Anna Kim",
            "img": "./assets/notifications-page-main/assets/images/avatar-anna-kim.webp",
            "href": "#"
          },
          "text": "left the group",
          "link": {
            "text": "Chess Club",
            "href": "#"
          },
          "time": "2 weeks ago",
          "hasBeenRead": false,
        },
      ]
    }
  },
  computed: {
    unreadNotificationCount() {
      return this.notifications && this.notifications.filter(n => n.isUnread).length
    }
  },
  methods: {
    markAllUnread() {
      this.notifications = this.notifications.map(n => ({...n, isUnread: false}))
    },
    handleNotificationClick(id) {
      this.notifications = this.notifications.map(n => (
        n.id === id
          ? {...n, isUnread: false}
          : n
      ))
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
