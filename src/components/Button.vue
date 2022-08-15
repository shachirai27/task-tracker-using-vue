<template>
    <button v-on:click="onClick" :style="{background: btnColor}" class="btn">{{btntext}}</button>
</template>

<script>
export default {
    name: 'ButtonComp',
    props: {
        btntext: String,
        btnColor:String
    },
    methods: {
        onClick() {
            this.$emit('btn-click')
        }
    }
}
</script>