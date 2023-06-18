<template>
    <div class="sun-container">
        <div class="sun" :style="{'background-color': `${this.color}`, 'box-shadow': `${this.shadow}` }"></div>
    </div>
</template>
<script>
export default {
    name: 'LightingSun',
    props: {
        hslcolor: {require: true, type: String}
    },
    data: function () {
        return {}
    },
    computed: {
        color() {
            return this.hslcolor;
        },
        shadow() {
            return `0px 0px 53px 13px ${this.hslcolor}`
        }
    }
}
</script>
<style scoped>
.sun-container {
    display: flex;
    width: 100%;
    justify-content: center;
    margin-bottom: 100%;
}
.sun {
    height: 127vw;
    width: 150vw;
    border-radius: 50%;
    position: fixed;
    top: -25%;
}
</style>