<script setup>
//props传入函数
const props = defineProps(["add"])
//传入input输入的值
function addTitle(e) {
    if (!e.target.value.trim()) { return }
    props.add(e.target.value)
    e.target.value = ""
}
</script>

<template>
    <div class="header">
        <input type="text" placeholder="请输入你的任务名称" @keyup.enter="addTitle" />
    </div>
</template>
<style scoped>
.header {
    display: flex;
    justify-content: flex-start;
    align-items: center;
    width: 100%;
    height: 20px;
}

.header input {
    width: 100%;
    height: 100%;
    font-size: 14px;
    outline: none;
    letter-spacing: .5px;
}
</style>