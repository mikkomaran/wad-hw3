<template>
    <div class="controls">
        <button id="profile-button" class="pill" :class="{active: profileIsActive}" @click="toggleActive(profileIsActive)">Profile</button>
        <button id="courses-button" class="pill" :class="{active: coursesIsActive}" @click="toggleActive(coursesIsActive)">Courses</button>
    </div>
</template>

<script>
    export default {
        name: "Controls",
        data: () => {
          return{
              profileIsActive: true,
              coursesIsActive: false,
          }
        },
       methods: {
            toggleActive: function (isActive) {
                if (!isActive) {
                    this.profileIsActive = !this.profileIsActive;
                    this.coursesIsActive = !this.coursesIsActive;
                    this.$emit('togglePage');
                }
            }
        }
    }
</script>

<style scoped>

    .controls .pill {
        border: 1px solid #cbcbcb;
        background-color: #eaeaea;
        padding: 10px;
        border-bottom-left-radius: 4px;
        border-bottom-right-radius: 4px;
        border-top: none;
        margin-top: -1px;
        outline: none !important;
    }

    .controls .pill.active {
        background-color: #ffffff;
        border-top: 1px solid #ffffff;
    }

    .controls .pill:hover {
        cursor: pointer;
    }

</style>