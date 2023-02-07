<script setup>
const props = defineProps(["data", "handlecheck", "del"])
const handelcheck = props.handlecheck
const del = props.del

</script>

<template>
    <div class="list" v-for="i in props.data" :key="i.id" @click="handelcheck(i.id)">
        <div>
            <input type="checkbox" :checked="i.done">
            <span>{{ i.title }}</span>
        </div>
        <button @click="del(i.id)">删除</button>
    </div>
</template>
<style scoped>
.list {
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-bottom: 1px solid rgba(0, 0, 0, .5);
    height: 20px;
}

span {
    font-size: 15px;
    font-weight: 500;
}

button {
    display: none;
    color: red;
    width: 40px;
    height: 20px;
    font-size: 10px;
    border: none;
    border-left: 0.5px solid rgba(0, 0, 0, .5);
    cursor: pointer;
}

.list:hover button {
    display: block;
}
</style>