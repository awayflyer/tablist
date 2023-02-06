<script setup>

</script>

<template>
    <div class="footer">
        <input type="checkbox">
        <span>已完成0/全部2</span>
        <button>清除已完成任务</button>
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