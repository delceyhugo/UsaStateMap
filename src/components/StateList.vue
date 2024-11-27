<script setup>
import { ref } from 'vue'
import json from '../assets/state.json'
const states = json.states
const dom = ref(null)

const emits = defineEmits(['onHover', 'onLeave'])

const handleOnHover = (e) => {
    let el = dom.value.querySelector('.' + e.target.id)
    el.classList.add('hovered')
    dom.value.scrollTo({top: el.offsetTop - (dom.value.offsetHeight / 2), behavior: 'smooth'})
}
const handleOnLeave = (e) => {
    dom.value.querySelector('.' + e.target.id).classList.remove('hovered')
}
defineExpose({handleOnHover, handleOnLeave})



</script>

<template>
    <div id="state-list">
        <ul ref="dom">
            <li @mouseenter="(e) => emits('onHover', e)" @mouseleave="(e) => emits('onLeave', e)" :id="state.code" v-for="state in states" :key="state.code" :class="state.status + ' ' + state.code">
                {{ state.name }}
            </li>
        </ul>
    </div>
</template>

<style lang="scss" scoped>
#state-list{
    min-width: 30%;
    height: 100%;
    ul{
        
        height: 100%;
        padding: 0px !important;
        display: flex;
        flex-direction: column;
        gap: 10px;
        padding: 20px;
        align-items: stretch;
        overflow-y: scroll;
        text-align: center;
        margin: 0px 20%;
        
        &::-webkit-scrollbar{
            width: 8px;
            background-color: #ffffff00;
        }
        &::-webkit-scrollbar-thumb{
            border-radius: 4px;
        }
        &::-webkit-scrollbar-track{
            background-color: transparent;
        }
        &:hover{
            &::-webkit-scrollbar-thumb{
                background-color: var(--color-white);
            }
        }
        li{
            display: flex;
            justify-content: center;
            align-items: center;
            list-style: none;
            color: white;
            font-size: 24px;
            font-family: "Barlow Condensed", serif;
            font-weight: 700;
            font-style: normal;
            text-align: center;
            border-radius: 5px;
            padding: 5px 0px;
            margin: 0px 5px;
            cursor: pointer;
            transition: all 0.2s ease-in-out;
            &:hover{
                background-color: var(--color-neutral);
            }
            &::before{
                content: "";
                display: inline-block;
                width: 15px;
                height: 15px;
                border-radius: 50%;
                margin-right: 10px;
            }
        }
        .available{
            background-color: var(--color-available);
            &::before{
                background-color: var(--color-available);
            }
        }
        .in-progress{
            background-color: var(--color-in-progress);
            &::before{
                background-color: var(--color-in-progress);
            }
        }
        .unavailable{
            background-color: var(--color-unavailable);
            &::before{
                background-color: var(--color-unavailable);
            }
        }
        .hovered{
            background-color: var(--color-neutral);
        }
    }
}
</style>