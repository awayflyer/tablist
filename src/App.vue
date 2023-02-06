<script setup>
import { reactive } from 'vue';
import List from './components/List.vue';
import MyFooter from './components/MyFooter.vue';
import Top from './components/Top.vue';
//创建数据
let tabdatas = reactive({
    info: [{
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
let tabdata = tabdatas["info"]

//新增数据
function add(value) {
    tabdata.unshift({ id: Math.random().toString(), title: value, done: false })
}
//checkbox开关关联数据
function handelcheck(id) {
    tabdata.forEach((item) => {
        if (id === item.id) {
            item.done = !item.done
        }
    })
}
//删除数据
function del(id) {
    tabdatas["info"] = tabdatas["info"].filter((item) => {
        return item.id !== id
    })
    console.log(tabdatas["info"]);
}
</script>

<template>
    <div class="box">
        <Top :add="add"></Top>
        <List :tabdata="tabdata" :handlecheck="handelcheck" :del="del"></List>
        <MyFooter></MyFooter>
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