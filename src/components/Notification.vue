<template>
   <div :class="{ notificationContainerActive: showAlert, notificationContainer: !showAlert }" @click="toggleAlert">
        <div class="image-container">
            <img class="notification-image" src="../assets/notifications-page-main/assets/images/avatar-mark-webber.webp" alt="Profile picture">
        </div>
        <div class="text-container">
            <span class="notification-text">
                <p class="notification-name">Mark Webber</p>
                <p class="notification-default">reacted to your recent post</p>
                <p class="notification-post">My first tournament today!</p>
                <span :class="{ notificationAlertActive: showAlert, notificationAlert: !showAlert }"></span>
            </span>
            <span class="notification-time">1m ago</span>
        </div>
   </div> 
</template>

<script>
export default {
    data() {
        return {
            showAlert: true
        }
    },
    methods: {
        toggleAlert() {
            this.showAlert = !this.showAlert
        }
    }
}
</script>

<style lang="scss">

.notificationContainerActive {
    margin: 8px 30px;
    padding: 20px 32px 20px 20px;
    width: fit-content;
    display: flex;
    align-items: center;
    justify-content: space-between;
    background-color: #F7FAFD;
    border-radius: 8px;
}

.notificationContainer {
    margin: 8px 30px;
    padding: 20px 32px 20px 20px;
    width: fit-content;
    display: flex;
    align-items: center;
    justify-content: space-between;
    background-color: #FFFFFF;
    border-radius: 8px;
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
    gap: 10px;
}

.text-container {
    min-width: 90%;
}

.notification-name {
    margin: 0;
    font-size: 16px;
    line-height: 20px;
    font-weight: 800;
    color: #1C202B;
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
}

.notification-time {
    font-size: 16px;
    line-height: 20px;
    font-weight: 500;
    color: #939CAD;
}

.notificationAlertActive {
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