<script setup>
    import {ref} from "vue"
    const count = ref(0)
    const props = defineProps(["name", "age"])
</script>
<template>
    <button>
    <slot/> {{props.age}}<br>{{props.name}}
    </button>
</template>