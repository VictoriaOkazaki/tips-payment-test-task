<template>
    <section class="rate">
        <Dots />
        <div class="rate__inner">
            <div class="rate__title h2">Rate your experience</div>
            <div class="rate__stars">
                <span v-for="(_cur, index) in  Array(5)" :key="index" @click="setActiveIndex(index)">
                    <Star :active="index <= activeIndex" />
                </span>
            </div>
            <div v-if="activeIndex >= 0" class="rate__addition">
                <div class="rate__addition-title p">What did you enjoy the most?</div>
                <ul class="rate__addition-list">
                    <li class="rate__addition-item">
                        <CustomCheckbox v-model="rate.service" />
                        <div class="rate__addition-item-text p">Service</div>
                    </li>
                    <li class="rate__addition-item">
                        <CustomCheckbox v-model="rate.cleanliness" />
                        <div class="rate__addition-item-text p">Cleanliness</div>
                    </li>
                    <li class="rate__addition-item">
                        <CustomCheckbox v-model="rate.atmosphere" />
                        <div class="rate__addition-item-text p">Atmosphere</div>
                    </li>
                    <li class="rate__addition-item">
                        <CustomCheckbox v-model="rate.foodQuality" />
                        <div class="rate__addition-item-text p">Food quality</div>
                    </li>
                </ul>
                <textarea v-model="rate.review" class="rate__addition-textarea p" rows="2"></textarea>
            </div>
        </div>
    </section>
</template>
<script>
export default {
    data() {
        return {
            rate: {
                stars: 0,
                service: false,
                cleanliness: false,
                atmosphere: false,
                foodQuality: false,
                review: ''
            }
        }
    },
    computed: {
        activeIndex() {
            return this.rate.stars - 1
        },
    },
    methods: {
        setActiveIndex(index) {
            console.log('setActive index', index)
            this.rate.stars = index + 1
        }
    }
}
</script>

<style lang="scss" scoped>
.rate {
    margin-top: -2.5px;
    margin-bottom: -2.5px;
    background-color: #fff;
    border-radius: 28px;

    &__inner {
        padding: 30px 33px;
    }

    &__title {
        color: $green;
        width: 100%;
        padding: 9px;
        text-align: center;
        background-color: $violet;
        border-radius: 8px;
        margin-bottom: 17px;
    }

    &__stars {
        width: 100%;
        display: flex;
        justify-content: space-between;
    }

    &__addition-title {
        margin-bottom: 34px;
        color: $violet;
        text-align: center;
        margin-top: 20px;
    }

    &__addition-list {
        margin-bottom: 20px;
    }

    &__addition-item {
        margin-bottom: 16px;
        display: flex;
        align-items: center;
    }

    &__addition-item-text {
        margin-left: 3px;
    }

    &__addition-textarea {
        border: 2px #DDE3F1 solid;
        background: none;

        border-radius: 10px;
        width: 100%;
        padding: 6px 16px;
        color: #808191;
        font-weight: 500;

        &:focus,
        &:active {
            background-color: #D3DBEC;
            border: none;
            outline: none !important;

        }
    }
}
</style>