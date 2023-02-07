<script setup>
import { reactive, watch } from 'vue';
import List from './components/List.vue';
import MyFooter from './components/MyFooter.vue';
import Top from './components/Top.vue';
//创建数据
let tabdata = reactive({
    info: [
        {
            id: "001",
            title: "吃饭",
            done: false
        }, {
            id: "002",
            title: "睡觉",
            done: false
        }, {
            id: "003",
            title: "玩游戏",
            done: false
        }
    ]
})
//新增数据
function add(value) {
    tabdata.info.unshift({ id: Math.random().toString(), title: value, done: false })
}
//checkbox开关关联数据
function handelcheck(id) {
    tabdata.info.forEach((item) => {
        if (id === item.id) {
            item.done = !item.done
        }
    })
}
//删除所点击的数据
function del(id) {
    // tabdatas.info = tabdatas.info.filter((item) => {
    //     return item.id !== id
    // })
    tabdata.info.forEach((item, index) => {
        if (id === item.id) {
            tabdata.info.splice(index, 1)
        }
    })
}
//控制全选取消,以T来接受总开关的true or false
function isAll(t) {
    if (!t) {
        tabdata.info.map((item) => {
            return item.done = true
        })
    }
    else {
        tabdata.info.map((item) => {
            return item.done = false
        })
    }
}
//控制删除已完成的数据
function clearIsDone() {
    tabdata.info = tabdata.info.filter(item => item.done === false)
}

</script>

<template>
    <div class="box">
        <Top :add="add"></Top>
        <List :tabdata="tabdata.info" :handlecheck="handelcheck" :del="del"></List>
        <MyFooter :tabdata="tabdata.info" :isAll="isAll" :clearIsDone="clearIsDone"></MyFooter>
    </div>

</template>

<style scoped>
.box {
    box-sizing: border-box;
    border: 1px solid;
    border-radius: 5px;
    padding: 10px 5px;
    margin: 0 auto;
    width: 400px;
    height: 200px;

}
</style>