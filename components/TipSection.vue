<template>
    <section class="tip">
        <div class="tip__inner">
            <div class="tip__title h2">Glad you enjoyed it today</div>
            <div class="tip__text p">Choose the amount you wish to tip and we will transfer it directly</div>
            <div class="tip__input-wrapper">
                <input :class="{ 'error': isError }" class="tip__input h2" type="text" :value="value"
                    @input="inputTipAmount" placeholder="Tip amount" inputmode="numeric" />
                <button v-if="value" class="tip__input-clear-btn" @click="setTipAmount(0)">
                    <img src="../assets/images/close.svg" alt="close">
                </button>
            </div>
            <div class="tip__btns-cont">
                <button class="tip__btn h2" :class="{ 'active': value == '2€' }" @click="setTipAmount('2€')">2€</button>
                <button class="tip__btn h2" :class="{ 'active': value == '5€' }" @click="setTipAmount('5€')">5€</button>
                <button class="tip__btn h2" :class="{ 'active': value == '10€' }" @click="setTipAmount('10€')">10€</button>
            </div>
        </div>
        <svg class="flt_svg" xmlns="http://www.w3.org/2000/svg">
            <defs>
                <filter id="flt_tag">
                    <feGaussianBlur in="SourceGraphic" stdDeviation="8" result="blur" />
                    <feColorMatrix in="blur" mode="matrix" values="1 0 0 0 0  0 1 0 0 0  0 0 1 0 0  0 0 0 19 -9"
                        result="flt_tag" />
                    <feComposite in="SourceGraphic" in2="flt_tag" operator="atop" />
                </filter>
            </defs>
        </svg>
    </section>
</template>

<script>
export default {
    props: ['value'],
    methods: {
        inputTipAmount(e) {
            this.setTipAmount(e.target.value);
        },
        setTipAmount(val) {
            this.$emit('input', val);
        }
    },
    computed: {
        isError() {
            if (!this.value) return false
            const num = Number(this.value.replace('€', ''))
            if (isNaN(num)) return true
            return false
        }
    }
}
</script>

<style lang="scss" scoped>
.flt_svg {
    visibility: hidden;
    position: absolute;
    width: 0px;
    height: 0px;
}

.tip {
    filter: url('#flt_tag');
    margin-bottom: -2.5px;

    &__inner {
        background-color: #fff;
        padding: 44px 20px 18px 20px;
        display: flex;
        flex-direction: column;
        align-items: center;
        clip-path: polygon(0 9%, 100% 0, 100% 100%, 0 100%);
        border-radius: 28px;
    }

    &__title {
        font-size: 24px;
        font-style: 120%;
        font-weight: 600;
        padding: 9px 15px;
        background-color: $violet-2;
        border-radius: 6px;
        text-align: center;
        color: $green;
        width: fit-content;
    }

    &__text {
        text-align: center;
        margin: 14px 0;
        color: $black;
    }

    &__input {
        padding: 14px 0 18px;
        width: 100%;
        border: 2px $violet solid;
        border-radius: 15px;
        text-align: center;
        margin-bottom: 15px;
        color: $violet;

        &::placeholder {
            color: rgba(186, 121, 254, 0.75);
        }

        &:focus {
            outline: none;
        }
    }

    &__input-wrapper {
        position: relative;
    }

    &__input-clear-btn {
        position: absolute;
        right: 10px;
        top: 10px;
    }

    &__btns-cont {
        width: 100%;
        display: flex;
        justify-content: space-between;
    }

    &__btn {
        padding: 14px 30px;
        background: rgba(186, 121, 254, 0.2);

        border-radius: 20px;
    }
}

.active {
    background-color: #96FF43;
}

.error {
    border: 2px red solid;
}
</style>
