<template>
    <div class="dots">
        <div class="dot" v-for="i in Array(18)" :key="i"></div>
    </div>
</template>
<script>
export default {
}
</script>

<style lang="scss" scoped>
.dots {
    padding: 0 40px;
    display: flex;
    justify-content: space-between;
    position: relative;
}

.dot {
    width: 5px;
    height: 5px;
    border-radius: 100%;
    background-color: $violet;
}
</style>