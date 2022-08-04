<script setup>
import zhCn from 'element-plus/lib/locale/lang/zh-cn'
const isCollapse = ref(false)
</script>

<template>
    <el-config-provider :locale="zhCn">
        <el-container>
            <el-header>
                <top-nav v-model:isCollapse="isCollapse" />
            </el-header>
            <el-container>
                <el-aside>
                    <collapse-menu :isCollapse="isCollapse" />
                </el-aside>
                <el-main>
                    <tree-card />
                    <data-table />
                </el-main>
            </el-container>
        </el-container>
    </el-config-provider>
</template>

<style lang="scss">
:root {
    user-select: none;
    height: 100%;

    body {
        margin: 0;
        padding: 0;
        height: 100%;

        #app {
            width: 100%;
            height: 100%;

            font-family: Avenir, Helvetica, Arial, sans-serif;
            -webkit-font-smoothing: antialiased;
            -moz-osx-font-smoothing: grayscale;
            text-align: center;
            color: #2c3e50;

            .el-container {
                width: 100%;
                height: 100%;

                .el-header {
                    display: flex;
                    justify-content: flex-start;
                    align-items: center;
                    background-color: #ec3a3b;
                }

                .el-aside {
                    width: auto;
                }

                .el-main {
                    display: flex;
                    flex: 1;

                }
            }
        }
    }

}
</style>
