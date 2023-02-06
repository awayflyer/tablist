<script setup>
import Item from './Item.vue'
const props = defineProps(["tabdata", "handlecheck", "del"])
</script>

<template>
    <div class="main">
        <Item :data="props.tabdata" :handlecheck="props.handlecheck" :del="props.del"></Item>
    </div>
</template>
<style scoped>
.main {
    overflow: auto;
    margin: 8px 0;
    width: 386px;
    height: 120px;
    border: 1px solid rgba(0, 0, 0, 0.7);
}
</style>