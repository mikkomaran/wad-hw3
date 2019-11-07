<template>
    <div id="profile-container" class="tab" :class="{active: isActive}" >
        <div id="profile">
            <div class="avatar">
                <img src="./../assets/me.png" id="picture" alt="My picture">
            </div>
            <div class="info">
                <ul>
                    <li id="name">{{user.firstname + " " + user.lastname}}</li>
                    <li id="birthdate">{{user.birthdate}}</li>
                    <li id="faculty">{{user.faculty}}</li>
                </ul>
            </div>
            <div id="gpa">
                <strong>{{user.gpa}}</strong>
            </div>
            <div class="clear-fix"></div>
        </div>
    </div>
</template>

<script>

    import User from "../models/User";

    export default {
        name: "Profile",
        data: () => {
            return {
                isActive: true,
                user: new User("John", "Doe", "11/10/1994", "Data Science", 0)
            }
        },
        methods: {
            toggleProfile: function () {
                this.isActive = !this.isActive;
            }
        }
    }
</script>

<style scoped>

    .tab {
        display: none;
    }

    .tab.active {
        display: block;
    }

    .clear-fix {
        clear: both;
    }

    #profile {
        border-bottom: 1px dashed #a7a7a7;
        padding-bottom: 10px;
        margin-bottom: 10px;
    }

    #profile div:not(.clear-fix) {
        height: 190px;
        float: left;
        position: relative;
    }

    #profile .avatar {
        width: 35%;
        text-align: center;
    }

    #profile .avatar img {
        width: 180px;
    }

    #profile .info {
        width: 45%;
    }

    #profile #gpa {
        width: 20%;
    }

    #profile #gpa strong {
        position: absolute;
        width: 100%;
        height: 60px;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        margin: auto auto;
        font-size: 60px;
        line-height: 60px;
        text-align: center;
    }

</style>