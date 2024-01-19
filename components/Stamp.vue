<template>
    <div class="circle-cont">
        <img src="../assets/images/logo.svg" alt="logo" class="logo">
        <img src="../assets/images/circle.svg" class="circle">
    </div>
</template>
<script>
export default {
}
</script>

<style lang="scss" scoped>
@keyframes rotateText {
    0% {
        transform: rotate(0deg);
    }

    100% {
        transform: rotate(360deg);
    }
}

.circle-cont {
    position: relative;
    width: 163px;
    height: 163px;
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 20;
}

.logo {
    width: 120px;
    height: 120px;
}

.circle {
    position: absolute;
    animation: rotateText 10s linear infinite;
}
</style>