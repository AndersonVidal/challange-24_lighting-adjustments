<template>
    <div class="slider-container">
        <ph-palette :size="25" class="color-icon" />
        <input type="range" v-model="value" class="slider" max="360" name="rangeInput" @change="takeColor"/>
    </div>
</template>
<script>
export default {
    name: 'LightingColorSlider',
    data: function () {
        return {
            value: 0
        }
    },
    methods: {
        takeColor(e) {
            const inputThumb = document.querySelector('input[name="rangeInput"]');
            inputThumb.style.setProperty("--SliderColor", `hsl(${this.value}, 100%, 50%)`);
            this.$emit('HSLColor', this.value);
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
        --SliderColor: hsl(0,100%,50%);
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
        background: linear-gradient(to right,
            hsl(0,100%,50%),
            hsl(60,100%,50%),
            hsl(120,100%,50%),
            hsl(180,100%,50%),
            hsl(240,100%,50%),
            hsl(300,100%,50%),
            hsl(360,100%,50%)
        );
        height: 5px;
        border-radius: 5px;
    }

    /******** Firefox ********/
    input[type="range"]::-moz-range-track {
        background: linear-gradient(to right,
            hsl(0,100%,50%),
            hsl(60,100%,50%),
            hsl(120,100%,50%),
            hsl(180,100%,50%),
            hsl(240,100%,50%),
            hsl(300,100%,50%),
            hsl(360,100%,50%)
        );
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