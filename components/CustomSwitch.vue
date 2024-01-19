<template>
    <div class="div">
        <label class="switch">
            <input type="checkbox" @click="toggleSwitch" :checked="value">
            <div class="slider round"></div>
        </label>
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
};
</script>
  
<style scoped>
.switch {
    position: relative;
    display: inline-block;
    width: 60px;
    height: 34px;
}

.switch input {
    display: none;
}

.slider {
    position: absolute;
    cursor: pointer;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: #ccc;
    -webkit-transition: 0.4s;
    transition: 0.4s;
}

.slider:before {
    position: absolute;
    content: "";
    height: 26px;
    width: 26px;
    left: 4px;
    bottom: 4px;
    background-color: white;
    -webkit-transition: 0.4s;
    transition: 0.4s;
}

input:checked+.slider {
    background: rgba(142, 108, 234, 0.40);

    ;
}

input:focus+.slider {
    box-shadow: 0 0 1px rgba(142, 108, 234, 0.40);

    ;
}

input:checked+.slider:before {
    -webkit-transform: translateX(26px);
    -ms-transform: translateX(26px);
    transform: translateX(26px);
}

.slider.round {
    border-radius: 34px;
}

.slider.round:before {
    border-radius: 50%;
}
</style>