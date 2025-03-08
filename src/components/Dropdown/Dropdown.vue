<template>
    <div class="dropdown">
        <div @click="toogleDropdown" class="showcase-result" :class="{'active': isOpen}">
            {{ selectedOption.map(option => option.name).join(', ') || placeholder }}
        </div>
        <ul class="dropdown-menu" :class="{'open': isOpen , 'close': !isOpen}">
            <li v-for="data in data" :key="data.id" @click="selectOption(data)" :class="{'active': selectedOption.some(option => option.id === data.id)}">{{data.name}}</li>
        </ul>
    </div>
</template>

<script>
import './dropdown.scss';
export default {
    name: 'DropdownMenu',
    props: {
        data:{
            type: Array,
            required: true
        },
        multiple:{
            type: Boolean,
            required: false
        },
        placeholder:{
            type: String,
            required: false
        }
    },
    data() {
        return {
            isOpen: false,
            selectedOption: []
        }
    },
    methods: {
        // methods go here
        toogleDropdown(){
            this.isOpen = !this.isOpen;
            if (this.isOpen) {
                document.addEventListener('click', this.handleOuterClick);
            } else {
                document.removeEventListener('click', this.handleOuterClick);
            }
        },
        selectOption(data){
            if(this.multiple){
                const index = this.selectedOption.findIndex(option => option.id === data.id);
                if(index > -1) {
                    this.selectedOption.splice(index, 1);
                } else {
                    this.selectedOption.push(data);
                }
                this.$emit('update:modelValue', this.selectedOption.map(option => option.id));
            }else{
                this.selectedOption = [data];
                this.isOpen = false;
                this.$emit('update:modelValue', data.id);
            }
        },
        handleOuterClick(event) {
            if (!this.$el.contains(event.target)) {
                this.isOpen = false;
            }
        }
    }
}
</script>

<style lang="scss" scoped>
/* Component-specific styles can still be defined here */
/* These will override the imported styles due to higher specificity of scoped styles */
</style>


