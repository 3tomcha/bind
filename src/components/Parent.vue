<template>
    <div v-for="(item, index) in loopObject" :key="index">
        <a href="" @click="changeTitle">parent</a>
        <el-input type="text" v-model="item.foods"/>
        {{item.foods}}
        <Child v-model:title="item.foods"/>
    </div>
</template>

<script>
import { ref, defineComponent, computed, toRefs } from 'vue'
import Child from './Child.vue'

export default defineComponent({
    components: {
        Child
    },
    setup() {
       const title = ref('')
       const titleComputed = computed({
           get: () => title.value,
           set: (value) => title.value = value
       })

       const changeTitle = () => {
           title.value = "abc"
       }

       const loopObject = [
           {
           foods: "gohan",
           drink: "coke"
           },
           {
           foods: "dorayaki",
           drink: "ocha"
           },
       ]

       return {
           titleComputed,
           changeTitle,
           loopObject
       }
    },
})
</script>
