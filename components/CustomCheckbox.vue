<template>
    <div class="checkbox-wrapper" @click="toggleSwitch">
        <input class="styled-checkbox" @click.stop="toggleSwitch" type="checkbox" :checked="value">
        <label @click.stop="toggleSwitch"></label>
        <slot />
    </div>
</template>

<script>
export default {
    props: ['value'],
    methods: {
        toggleSwitch() {
            this.$emit('input', !this.value);
        },
    },
}
</script>

<style lang="scss" scoped>
.checkbox-wrapper {
    display: flex;
    align-items: center;
}

.styled-checkbox {
    position: absolute; // take it out of document flow
    opacity: 0; // hide it

    &+label {
        position: relative;
        cursor: pointer;
        padding: 0;
    }

    // Box.
    &+label:before {
        content: '';
        margin-right: 14px;
        display: inline-block;
        vertical-align: text-top;
        width: 24px;
        height: 24px;
        background: #D3DBEC;
        border-radius: 8px;
    }

    // Box hover
    &:hover+label:before {
        background: #D3DBEC;
    }

    // Box checked
    &:checked+label:before {
        background: #2CEF34;

    }

    // Disabled state label.
    &:disabled+label {
        color: #b8b8b8;
        cursor: auto;
    }

    // Disabled box.
    &:disabled+label:before {
        box-shadow: none;
        background: #ddd;
    }

    // Checkmark. Could be replaced with an image
    &:checked+label:after {
        content: '';
        position: absolute;
        left: 7px;
        top: 11px;
        background: white;
        width: 2px;
        height: 2px;
        box-shadow:
            2px 0 0 white,
            4px 0 0 white,
            4px -2px 0 white,
            4px -4px 0 white,
            4px -6px 0 white,
            4px -8px 0 white;
        transform: rotate(45deg);
    }
}
</style>