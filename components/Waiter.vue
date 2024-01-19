<template>
    <section class="waiter">
        <div class="waiter__inner">
            <div class="waiter__img-cont">
                <img class="waiter__img" src="~/assets/images/waiter.png" alt="waiter" />
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
            </div>
            <div class="waiter__text-cont">
                <div class="waiter__text h1">Gabrielle</div>
                <div class="waiter__text p">was your waiter</div>
            </div>
            <div class="waiter__under-text"></div>
            <Stamp class="stamp" />
        </div>

    </section>
</template>
<script>
export default {}
</script>

<style lang="scss" scoped>
.stamp {
    position: absolute;
    right: 8px;
    bottom: -14px;
}

.waiter {
    &__inner {
        position: relative;
    }

    &__img {
        border-radius: 28px;
        clip-path: polygon(0 0, 100% 0, 100% 95%, 0% 100%);
    }

    &__img-cont {
        filter: url('#flt_tag');
        z-index: 10;
        position: relative;
    }

    &__text-cont {
        position: absolute;
        bottom: 36px;
        left: -20px;
        background-color: $violet;
        rotate: -5.27deg;
        border-radius: 8px;
        padding: 24px 25px 19px 45px;
        width: 246px;
        transform-origin: left;
        z-index: 10;
    }

    &__text {
        rotate: 5.27deg;
        color: #fff;
    }

    &__under-text {
        background-color: #6238D3;
        width: 20px;
        height: 7px;
        position: absolute;
        bottom: calc(36px - 5px);
        left: -10px;
        rotate: 8deg;
    }
}

.flt_svg {
    visibility: hidden;
    position: absolute;
    width: 0px;
    height: 0px;
}
</style>