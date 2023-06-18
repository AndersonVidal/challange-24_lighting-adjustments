<template>
    <div>
        <LightingColorSlider class="slide-input" @HSLColor="changeColor"/>
        <LightingBrightnessSlider class="slide-input" :initValue="50" @sliderValue="changeBrightness"/>
        <LightingBrightnessSlider class="slide-input" :initValue="100" :contrast="true" @sliderValue="changeContrast" />
    </div>
</template>
<script>
import LightingColorSlider from './LightingColorSlider.vue'
import LightingBrightnessSlider from './LightingBrightnessSlider.vue'
export default {
    name: 'LightingForm',
    components: {
        LightingColorSlider,
        LightingBrightnessSlider
    },
    data: function () {
        return {
            color: 0,
            brightness: 0,
            contrast: 0
        }
    },
    methods: {
        changeColor(color) {
            this.color = color;
            this.$emit('HSLValue', this.takeHsl());
        },
        changeBrightness(brightness) {
            this.brightness = brightness;
            this.$emit('HSLValue', this.takeHsl());
        },
        changeContrast(contrast) {
            this.contrast = contrast;
            this.$emit('HSLValue', this.takeHsl());
        },
        takeHsl() {
            return `hsl(${color}, ${contrast}%, ${brightness}%)`;
        }
    }
}
</script>
<style scoped>
.slide-input:not(:last-child) {
    margin-bottom: 84px;
}
</style>