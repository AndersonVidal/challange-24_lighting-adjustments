<template>
    <div class="layout">
        <LightingSun :hslcolor="hsl" />
        <div class="title-box">
            <label>Ajustes de Iluminação</label>
        </div>
        <LightingForm @HSLValue="getHSLValue"/>
    </div>
</template>
<script>
import LightingForm from './components/LightingForm.vue'
import LightingSun from './components/LightingSun.vue'
export default {
    name: 'LightingAdjustments',
    components: {
        LightingForm,
        LightingSun
    },
    data: function () {
        return {
            hsl: 'hsl(0, 100%, 50%)'
        }
    },
    methods: {
        getHSLValue(value) {
            this.hsl = value;
        }
    }
}
</script>
<style scoped>
.title-box {
    width: 100%;
    text-align: center;
    margin-bottom: 30%;
    margin-top: 115%;
}

.title-box > label {
    font-family: 'Raleway';
    font-style: normal;
    font-weight: 300;
    font-size: 32px;
    line-height: 38px;
    color: white;
}
</style>