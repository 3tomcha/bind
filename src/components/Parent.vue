<template>
    <div>
        <a href="" @click="changeTitle">parent</a>
        <input type="text" v-model="titleComputed">
        {{titleComputed}}
        <Child v-model:title="titleComputed"/>
    </div>
</template>

<script>
import { ref, defineComponent, computed } from 'vue'
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

       return {
           titleComputed,
           changeTitle
       }
    },
})
</script>
