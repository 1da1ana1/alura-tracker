<template>  
    <div class="box has-text-weight-bold">
        <slot></slot>
    </div>
</template>

<script lang="ts">
import { defineComponent, DefineComponent } from 'vue';

export default defineComponent({
    name: 'boxMessage'
})
</script>
