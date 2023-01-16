<template>
  <div class="container">
    <div class="notifications-container">
      <header class="notifications-header">
      <div class="notifications-headerTitle">
        <h1 class="notifications-title">Notifications</h1>
        <span class="notifications-number">{{ unreadNotificationCount }}</span>
      </div>
      <button id="markAll" @click="markAllUnread">
        <span class="notifications markAllAsRead">Mark all as read</span>
      </button>
    </header>
    <div class="notifications-cardsContainer">
      <div v-for="n in notifications" :key="n.id" @click="handleNotificationClick(n.id)" class="notificationContainer" :class="{ 'unread': n.isUnread }">
        <div class="image-container">
          <img :src="n.author.src" :alt="n.author.name" class="notification-image" />
        </div>
        <div class="text-container">
          <div class="notification-text">
            <p class="notification-name">
              <a :href="n.author.href">{{ n.author.name }}</a>
            </p>
            <p class="notification-default">{{ n.text }}</p>
            <p class="notification-post">
              <a v-if="n.link" :href="n.link.href"> {{ n.link.text }}</a>
            </p>
            <span v-if="n.isUnread" class="isUnread"></span>
          </div>
          <span class="notification-time">{{ n.time }}</span>
          <p v-if="n.privateMessage" class="notification-message">{{ n.privateMessage }}</p>
        </div>
        <a v-if="n.image" :href="n.image.href">
          <img :src="n.image.src" :alt="n.image.alt" />
        </a>
      </div>
    </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  components: {},
  data() {
    return {
      notifications: [
        {
          "id": "1",
          "author": {
            "name": "Mark Webber",
            "src": require("../src/assets/notifications-page-main/assets/images/avatar-mark-webber.webp"),
            "href": "#"
          },
          "text": "reacted to your recent post",
          "link": {
            "text": "My first tournament today!",
            "href": "#"
          },
          "time": "1m ago",
          "isUnread": true,
          "privateMessage" : "",
        },
        {
          "id": "2",
          "author": {
            "name": "Angela Gray",
            "src": require("../src/assets/notifications-page-main/assets/images/avatar-angela-gray.webp"),
            "href": "#"
          },
          "text": "followed you",
          "link": {
            "text": "",
            "href": "#"
          },
          "time": "5m ago",
          "isUnread": true,
          "privateMessage" : "",
        },
        {
          "id": "3",
          "author": {
            "name": "Jacob Thompson",
            "src": require("../src/assets/notifications-page-main/assets/images/avatar-jacob-thompson.webp"),
            "href": "#"
          },
          "text": "has joined your group",
          "link": {
            "text": "Chess Club",
            "href": "#"
          },
          "time": "1 day ago",
          "isUnread": true,
          "privateMessage" : "",
        },
        {
          "id": "4",
          "author": {
            "name": "Rizky Hasanuddin",
            "src": require("../src/assets/notifications-page-main/assets/images/avatar-rizky-hasanuddin.webp"),
            "href": "#"
          },
          "text": "sent you a private message",
          "link": {
            "text": "",
            "href": "#"
          },
          "time": "5 days ago",
          "isUnread": false,
          "privateMessage" : "Hello, thanks for setting up the Chess Club. I've been a member for a few weeks now and I'm already having lots of fun and improving my game.",
        },
        {
          "id": "5",
          "author": {
            "name": "Kimberly Smith",
            "src": require("../src/assets/notifications-page-main/assets/images/avatar-kimberly-smith.webp"),
            "href": "#"
          },
          "text": "commented on your picture",
          "link": {
            "text": "",
            "href": "#"
          },
          "time": "1 week ago",
          "isUnread": false,
          "privateMessage" : "",
        },
        {
          "id": "6",
          "author": {
            "name": "Nathan Peterson",
            "src": require("../src/assets/notifications-page-main/assets/images/avatar-nathan-peterson.webp"),
            "href": "#"
          },
          "text": "reacted to your recent post",
          "link": {
            "text": "5 end-game strategies to increase your win rate",
            "href": "#"
          },
          "time": "2 weeks ago",
          "isUnread": false,
          "privateMessage" : "",
        },
        {
          "id": "7",
          "author": {
            "name": "Anna Kim",
            "src": require("../src/assets/notifications-page-main/assets/images/avatar-anna-kim.webp"),
            "href": "#"
          },
          "text": "left the group",
          "link": {
            "text": "Chess Club",
            "href": "#"
          },
          "time": "2 weeks ago",
          "isUnread": false,
          "privateMessage" : "",
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
  margin: auto;
  padding: 30px 20px;
  min-width: 516px;
  max-width: 900px;
  display: flex;
  flex-direction: column;
  align-self: center;
  align-items: center;
  background-color: white;
  border-radius: 15px;
  box-shadow: 0px 20px 60px rgba(73, 97, 168, 0.05);
}

.notificationContainer {
    margin: 8px 30px;
    padding: 20px 32px 20px 20px;
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: flex-start;
    background-color: #FFFFFF;
    border-radius: 8px;
    gap: 20px;
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
  // margin: 8px 30px;
  // width: 90%;
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

.image-container {
    max-width: 5%;
}

.notification-image {
    width: 100%;
}

.notification-text {
    display: flex;
    align-items: center;
    flex-wrap: wrap;
    gap: 7px;
}

.text-container {
    display: flex;
    flex-direction: column;
    gap: 5px;
    max-width: 90%;
}

.notification-name {
    margin: 0;
    font-size: 16px;
    line-height: 20px;
    font-weight: 800;
    color: #1C202B;

    transition: all ease-in-out 0.3s;

    &:hover {
        color: #0A327B;
        cursor: pointer;
    }

    a {
      text-decoration: none;
      color: inherit;
    }
}

.notification-default {
    margin: 0;
    font-size: 16px;
    line-height: 20px;
    font-weight: 500;
    color: #5E6778;
}

.notification-post {
    margin: 0;
    font-size: 16px;
    line-height: 20px;
    font-weight: 800;
    color: #5E6778;
    transition: all ease-in-out 0.3s;

    &:hover {
        color: #0A327B;
        cursor: pointer;
    }

    a {
      text-decoration: none;
      color: inherit;
    }
}

.notification-group {
    margin: 0;
    font-size: 16px;
    line-height: 20px;
    font-weight: 800;
    color: #0A327B;

    transition: all ease-in-out 0.3s;

    &:hover {
        color: #0A327B;
        cursor: pointer;
    }
}

.notification-time {
    font-size: 16px;
    line-height: 20px;
    font-weight: 500;
    color: #939CAD;
}

.notification-message {
    margin: 20px 0 0 0 ;
    padding: 20px;
    width: 90%;
    border: 1px solid #DDE7EE;
    border-radius: 5px;
    font-size: 16px;
    line-height: 20px;
    font-weight: 500;
    color: #5E6778;
    transition: all ease-in-out 0.3s;

    &:hover {
        background-color: #DDE7EE;
        cursor: pointer;
    }
}

.unread {
  background-color: #F7FAFD;
}

.isUnread {
    height: 10px;
    width: 10px;
    background-color: #F65552;
    border-radius: 50%;
    display: inline-block;
}

.notificationAlert {
    height: 10px;
    width: 10px;
    background-color: transparent;
    border-radius: 50%;
    display: inline-block;
}

</style>
