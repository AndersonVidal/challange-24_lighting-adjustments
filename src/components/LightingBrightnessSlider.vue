<template>
    <div class="slider-container">
        <ph-circle-half v-show="contrast" :size="25" class="color-icon" />
        <ph-sun v-show="!contrast" :size="25" class="color-icon" />
        <input type="range" v-model="value" class="slider" max="100" name="rangeInput" @change="takeValue"/>
    </div>
</template>
<script>
export default {
    name: 'LightingBrightnessSlider',
    props: {
        contrast: {require: false, default: false, type: Boolean},
        initValue: {require: false, default: 0, type: Number}
    },
    data: function () {
        return {
            value: this.initValue
        }
    },
    methods: {
        takeValue(e) {
            this.$emit('sliderValue', this.value);
        }
    }
}
</script>
<style scoped>
    .slider-container {
        display: flex;
        flex-direction: row;
    }
    .color-icon {
        margin-right: 10px;
        color: white;
    }
    .slider {
        --SliderColor: #151515;
    }

    input[type="range"] {
        -webkit-appearance: none;
        appearance: none;
        background: transparent;
        cursor: pointer;
        width: 100%;
        --SliderBorderWidth: 2px;
    }

    input[type="range"]:hover {
        --SliderBorderWidth: 1px;
    }

    input[type="range"]:active {
        --SliderBorderWidth: 3px;
    }

    /***** Chrome, Safari, Opera, and Edge Chromium *****/
    input[type="range"]::-webkit-slider-runnable-track {
        background: #D9D9D9;
        height: 5px;
        border-radius: 5px;
    }

    input[type="range"]::-moz-range-track {
        background: #D9D9D9;
        height: 5px;
        border-radius: 5px;
    }

    /***** Chrome, Safari, Opera, and Edge Chromium *****/
    input[type="range"]::-webkit-slider-thumb {
        -webkit-appearance: none; /* Override default look */
        appearance: none;
        margin-top: -6.7px; /* Centers thumb on the track */
        background-color: var(--SliderColor);
        height: 18px;
        width: 18px;
        border-radius: 50%;
        border-style: solid;
        border-width: var(--SliderBorderWidth);
        border-color: white;
    }
    /***** Firefox *****/
    input[type="range"]::-moz-range-thumb {
        border: none; /*Removes extra border that FF applies*/
        border-radius: 0; /*Removes default border-radius that FF applies*/
        background-color: var(--SliderColor);
        height: 18px;
        width: 18px;
        border-radius: 50%;
        border-style: solid;
        border-width: var(--SliderBorderWidth);
        border-color: white;
    }
</style>