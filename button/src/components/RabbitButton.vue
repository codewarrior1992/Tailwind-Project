<template>
    <div
    :class="[
        'px-3 py-3',
        'rounded-md font-bold',
        'bg-gray-400 hover:bg-gray-300 active:bg-gray-500',
        'hover:scale-105 active:scale-95',
        'transition-all',
        'cursor-pointer',
        'flex justify-between',
        'text-white',
        colorSelector
    ]"
    >
    <slot name="iconLeft" />
    {{ text }}
    <slot name="iconRight" />
    </div>
</template>

<script>
export default {
    name: "RabbitButton",
    props:{
        text: {
            default: "按鈕"
        },
        color: {
            default: "gray"
        },
    },
    computed: {
        colorSelector() {
            return {
                gray: 'bg-gray-400 hover:bg-gray-300 active:bg-gray-500',
                green: 'bg-green-400 hover:bg-green-300 active:bg-green-500',
                blue: 'bg-blue-400 hover:bg-blue-300 active:bg-blue-500',
                red: 'bg-red-400 hover:bg-red-300 active:bg-red-500',
                yellow: 'bg-yellow-400 hover:bg-yellow-300 active:bg-yellow-500',
            }[this.color]
        }
    }
}
</script>