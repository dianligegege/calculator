<template>
    <p>nameRef: {{ nameRef }}</p>
    <p>nameDefault: {{ nameDefault }}</p>
</template>

<script>
import { ref, onMounted, watch, toRefs, computed } from 'vue';

export default {
    props: {
        name: {
            default: '',
            type: String,
        },
    },
    setup(props) {
        // 使用 setup 把由 props.name 变化引起的一系列动作都集合在了一起
        const { name } = toRefs(props);

        let nameRef = ref('');
        let nameDefault = '';
        const getName = () => {
            console.log('调用');
            if (name === 'dianli') {
                nameRef = 'dianli';
                nameDefault = 'dianli';
            } else {
                nameRef = 'zhangli';
                nameDefault = 'zhangli';
            }
        }

        // mounted 时调用
        onMounted(getName);

        // watch 监听
        watch(name, getName);

        // computed 计算属性
        const nameComputed = computed(() => {
            return `nameRef: ${nameRef.value}, nameDefault: ${nameDefault}`
        });

        return {
            getName,
            nameRef,
            nameDefault,
            nameComputed,
        };
    },
};
</script>
