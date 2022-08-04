<script  setup>
defineProps({
    isCollapse: {
        type: Boolean,
        default: false,
    },
})

</script>

<template>
    <el-menu background-color="#fdf4ef"
             active-text-color="#fff"
             unique-opened
             :collapse="isCollapse">
        <el-sub-menu index="1">
            <template #title>
                <el-icon>
                    <Star />
                </el-icon>
                <span>党组织规范化建设</span>
            </template>
            <el-menu-item-group>
                <el-menu-item index="1-1"><span>——</span>党组织规范化建设</el-menu-item>
                <el-menu-item index="1-2"><span>——</span>党组织规范化建设</el-menu-item>
            </el-menu-item-group>
        </el-sub-menu>

        <el-sub-menu index="2">
            <template #title>
                <el-icon>
                    <location />
                </el-icon>
                <span>党员管理</span>
            </template>
            <el-menu-item-group>
                <el-menu-item index="2-1"><span>——</span>党员基本情况</el-menu-item>
                <el-menu-item index="2-2"><span>——</span>发展党员</el-menu-item>
                <el-menu-item index="2-3"><span>——</span>民主评议党员</el-menu-item>
                <el-menu-item index="2-4"><span>——</span>党费使用情况报告</el-menu-item>
            </el-menu-item-group>
        </el-sub-menu>

        <el-menu-item index="3"
                      class="topActive">

            <el-icon>
                <document />
            </el-icon>
            <template #title>
                党建品牌创建
            </template>
        </el-menu-item>
    </el-menu>
</template>



<style lang="scss" scoped>
.el-menu {
    height: 100%;

    &:not(.el-menu--collapse) {
        width: 300px;

        .el-menu-item.topActive.is-active>i {
            color: #fff;
        }
    }

    .el-sub-menu__title {
        &:hover {
            color: #fff;
            background-image: linear-gradient(to right, #ec3a3b, #fdeeee)
        }
    }

    .el-sub-menu {
        :deep(.el-menu-item-group__title) {
            padding: 0
        }

        :deep(.el-sub-menu__icon-arrow) {
            transform: none;
            color: #f13637;
            width: 0;
            height: 0;
            border-top: 8px solid transparent;
            border-left: 8px solid #f13637;
            border-bottom: 8px solid transparent;
        }

        &.is-active,
        &.is-opened {
            :deep(.el-sub-menu__title) {
                color: #fff;
                background-image: linear-gradient(to right, #ec3a3b, #fdeeee)
            }

            :deep(.el-sub-menu__icon-arrow) {
                transform: rotateZ(90deg)
            }
        }

    }

    .el-menu-item {

        &.is-active,
        &:hover {
            color: #f13637;
            background-color: #fdf4ef;
        }

        span {
            color: #f13637;
            padding-right: 15px;
            border-left: #f13637 solid 1px;
        }
    }

    .el-menu-item.topActive {

        i,
        & {
            border: none;
            color: #303133;
        }


        &.is-active {
            background-image: linear-gradient(to right, #ec3a3b, #fdeeee);

            i,
            & {
                color: #fff;

            }
        }
    }
}
</style>