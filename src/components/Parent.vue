<script setup lang="ts">
import { ref, computed} from 'vue'
import Child from './Child.vue'
const title = ref('')
const titleComputed = computed({
    get: () => title.value,
    set: (value) => title.value = value
})

const changeTitle = () => {
    title.value = "abc"
}

const loopObject = ref([
    {
    foods: "gohan",
    drink: "coke"
    },
    {
    foods: "dorayaki",
    drink: "ocha"
    },
])       
</script>

<template>
    <div v-for="(item, index) in loopObject" :key="index">
        <a href="" @click="changeTitle">parent</a>
        <el-input type="text" v-model="item.foods"/>
        {{item.foods}}
        <Child v-model:title="item.foods"/>
    </div>
</template>

