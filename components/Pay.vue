<template>
    <section class="pay">
        <Dots />
        <div class="pay__inner">
            <div class="pay__top">
                <div class="pay__content">
                    <div class="pay__content-title p">I want Philip to get the full amount</div>
                    <div class="pay__content-text">You compensate service commission, and {{ commission }} € will be debited
                        from your
                        card.</div>
                </div>
                <CustomSwitch v-model="isChecked" />
            </div>

            <button :disabled="!isAgree" class="apple-pay button">
                <img src="../assets/images/apple-pay.svg" alt="apple-pay">
            </button>
            <button :disabled="!isAgree" class="card-pay button">Pay by card</button>
            <div class="pay__bottom">
                <CustomCheckbox v-model="isAgree">
                    <div class="pay__bottom-text">I agree with <a>Terms & Conditions</a>
                        and <a>Privacy policy</a></div>
                </CustomCheckbox>
            </div>
        </div>
    </section>
</template>
<script>
export default {
    props: ['tipAmount'],
    data() {
        return {
            isChecked: false,
            isAgree: false
        }
    },
    computed: {
        commission() {
            if (!this.tipAmount) return 0
            const num = Number(this.tipAmount.replace('€', ''))
            if (isNaN(num)) return 0

            if (!this.isChecked) return num
            return (num * 1.1).toFixed(2)
        }
    }
}
</script>

<style lang="scss" scoped>
a {
    border-bottom: 0.5px #808191 solid;
    padding-bottom: 0.4px;
}

.pay {
    background-color: #fff;
    margin-top: -2.5px;
    border-radius: 28px;

    &__inner {
        padding: 30px 24px;
        display: flex;
        flex-direction: column;
    }

    &__top {
        margin-bottom: 18px;
        display: flex;
        justify-content: space-between;
    }

    &__content {
        display: flex;
        flex-direction: column;
        margin-right: 8px;
    }

    &__content-title {
        color: $black;
        margin-bottom: 6px;
    }

    &__content-text {
        font-size: 11px;
        font-style: normal;
        font-weight: 500;
        color: #808191;
    }

    &__bottom {
        display: flex;
    }

    &__bottom-text {
        color: #808191;
        font-size: 12px;
        font-weight: 500;
    }
}

.button {
    border-radius: 22px;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 18px 0;
    width: 100%;
}

.button:disabled {
    opacity: 0.6;
}

.button:active {
    opacity: 0.8;
}

.apple-pay {
    border: 2px #DDE3F1 solid;
    margin-bottom: 13px;
    background-color: #fff;
}

.card-pay {
    background-color: #96FF43;
    color: #3A414A;
    filter: drop-shadow(0px 15px 20px #c8f1a6);
    font-size: 18px;
    font-weight: 600;
    margin-bottom: 20px;
}
</style>