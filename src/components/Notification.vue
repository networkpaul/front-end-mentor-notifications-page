<template>
   <div :class="{ notificationContainerActive: showAlert, notificationContainer: !showAlert }" @click="toggleAlert">
        <div :class="{ 'alignSelf': message }" class="image-container">
            <img class="notification-image" :src="pictureFilename" alt="Profile picture">
        </div>
        <div class="text-container">
            <span class="notification-text">
                <p class="notification-name" v-if="name">{{ name }}</p>
                <p class="notification-default" v-if="defaultText">{{ defaultText }}</p>
                <p class="notification-post" v-if="post">{{ post }}</p>
                <p class="notification-group" v-if="group">{{ group }}</p>
                <span :class="{ notificationAlertActive: showAlert, notificationAlert: !showAlert }"></span>
            </span>
            <span class="notification-time">{{ time }}</span>
            <p class="notification-message" v-if="message">{{ message }}</p>
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
    props: [ 'pictureFilename', 'name', 'defaultText', 'post', 'group', 'time', 'message' ],
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
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: flex-start;
    background-color: #F7FAFD;
    border-radius: 8px;
    gap: 20px;
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

.alignSelf {
    align-self: flex-start;
}
</style>