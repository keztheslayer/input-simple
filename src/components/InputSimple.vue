<template>
    <div class="input-simple">
        <input 
            v-bind="$attrs"
            @input="input( $event.target.value )"
            :value="value"
        >
        <span
            v-if="value.length" 
            class="clear-button"
            @click="clear"
        />
    </div>
</template>
<script>
export default {
    inheritAttrs: false,
    beforeMount() {
        this.value = this.modelValue;
    },
    props: {
        modelValue: {
            default: ''
        }
    },
    methods: {
        input( value ) {
            this.value = value;
            this.$emit('update:modelValue', value);
        },
        clear() {
            this.input('');
        },
    }
}
</script>
<style scoped>
input {
    width: 100%;
    padding: 6px 12px;
    border-radius: 4px;
}
.input-simple {
    position: relative;
}
.clear-button {
    display: block;
    width: 16px;
    height: 16px;
    background: url('../assets/x-mark.svg') no-repeat center/contain;
    cursor: pointer;
    position: absolute;
    top: 9px;
    right: 12px;
}
.clear-button:hover {
    opacity: 0.5;
}
</style>