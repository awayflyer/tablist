<script setup>
const props = defineProps(["tabdata", "isAll", "clearIsDone"])
//筛选出已完成的数量
function isDone() {
    return props.tabdata.filter((item) => {
        return item.done == true
    }).length
}
//已完成数量等于总数量，则全选
function handelCheckDone() {
    if (props.tabdata.length !== 0) {
        return isDone() === props.tabdata.length
    }
    return
}
</script>

<template>
    <div class="footer">
        <input type="checkbox" :checked="handelCheckDone()" @change="isAll(handelCheckDone())">
        <span>已完成{{ isDone() }}/全部{{ props.tabdata.length }}</span>
        <button @click="clearIsDone">清除已完成任务</button>
    </div>

</template>
<style scoped>
.footer {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-top: 10px;
}

span {
    margin-left: -150px;
    font-size: 14px;
}

button {
    border-width: 1px;
    border-radius: 3px;
    background-color: red;
    color: #ffffff;
    cursor: pointer;
}
</style>