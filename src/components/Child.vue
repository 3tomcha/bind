<template>
    <div>
        <p>child</p>
        <el-input type="text" v-model="titleComputed"/>
    </div>
</template>

<script>
import { computed, defineComponent, toRefs } from 'vue'

export default defineComponent({
    props: {
        title: String
    },
    setup(props, { emit }) {
        const { title } = toRefs(props)
        const titleComputed = computed({
            get: () => title.value,
            set: (value) => emit('update:title',value)
        })

        return {
            titleComputed
        }
    },
})
</script>
