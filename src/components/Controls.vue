<template>
    <div class="controls">
        <button id="profile-button" class="pill active">Profile</button>
        <button id="courses-button" class="pill">Courses</button>
    </div>
</template>

<script>
    export default {
        name: "Controls"
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
        background-color: #ffffff;
    }

</style>