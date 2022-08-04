
<script setup>
const emits = defineEmits(['update:isCollapse'])
const props = defineProps({
    isCollapse: {
        type: Boolean,
        default: false,
    },
})

const handleClick = () => emits('update:isCollapse', !props.isCollapse)

</script>
<template>
    <el-icon :size="25"
             color="#fff"
             @click="handleClick">
        <Expand v-show="isCollapse" />
        <Fold v-show="!isCollapse" />
    </el-icon>
</template>