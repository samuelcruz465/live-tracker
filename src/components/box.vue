<template>
    <div class="box has-text-weight-bold">
        <slot>
        </slot>
    </div>
    </template>

<script lang="ts">
    import { defineComponent } from 'vue';
    export default defineComponent({
        name: 'UseBox',
    })
</script>
<style scoped>
.box{
    background: #f7e973
    }
</style><script></script>