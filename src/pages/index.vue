<template>
    <div>
        <Demo
            :name="name"
        />
        <button @click="name = 'dianli'">dianli</button>
        <button @click="name = 'zhangli'">zhangli</button>
    </div>
</template>

<script>
import Demo from '@/components/demo.vue'

export default {
    components: { Demo },
    data() {
        return {
            name: '',
        };
    }
}
</script>