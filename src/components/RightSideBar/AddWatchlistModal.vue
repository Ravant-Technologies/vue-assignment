<template>
    <div>
        <Modal :isOpen="this.isOpen" v-if="isOpen" @hide="onClose">
            <transition name="modal-slide">
                <div class="bg-dapp-black-1 p-5 rounded-2xl">
                    <div  v-if="isOpen" class="w-[90vw] max-h-screen overflow-y-auto max-w-7xl md:w-[600px] lg:w-[1078px] xl:w-[1200px] transform overflow-hidden py-8 md:py-9 px-6 sm:px-9 md:px-10 text-left transition-all relative">
                        <button @click="onClose"
                        class="text-2xl font-normal bg-dapp-white-10 w-12 h-12 rounded-lg text-white hover:bg-dapp-red flex justify-center items-center absolute top-5 right-5 z-10">
                            <Icon icon="fluent-mdl2:cancel" />
                        </button>
                    <h2 class="text-xl lg:text-2xl 2xl:text-3xl font-medium leading-[1.2] text-white">Add Symbol</h2>
                    </div>
                    <div>
                        <div class="relative mt-7 text-gray-600">
                            <button type="submit" class="absolute left-0 top-1/2 -translate-y-1/2 ml-4 text-white text-xl">
                                <Icon icon="fe:search" />
                            </button>
                            <input
                                class="border-none bg-[#ffffff10] h-12 lg:h-[50px] 2xl:h-16 px-4 pl-12 rounded-xl text-base focus:outline-none placeholder:text-[#999999] w-full text-white"
                                type="search" name="search" placeholder="Search" autocomplete="off" />
                        </div>
                        <div >
                            <Chip v-for="(chip, index) in chips" :key="index" :active="chip.active" @onClick="onChipClick">
                                {{ chip.label }}
                            </Chip>
                             <!-- <Chip v-for="value in data" :key="index" :active="value.active" @onClick="onChipClick">
                                {{ chip.label }}
                            </Chip> -->
                        </div>
                        <div class="mt-7 flex flex-col">
                            <ListItem v-for="value in data" :key="value.index" :name="value.symbol" :iconUrl="value.iconUrl"/>
                        </div>
                    </div>
                </div>
            </transition>
        </Modal>
    </div>
</template>

<script>
import Modal from '../others/modal.vue';
import Card from './card.vue';
import { Icon } from '@iconify/vue2';
import ListItem from "./ListItem.vue"; 
import Chip from "./Chip.vue"; 

export default {
    components: {
        Modal,
        Card,
        Icon,
        Chip,
        ListItem
    },
    data() {
        return {
            chips: [
                { label: "All", active: true },
                { label: "Stocks", active: false },
                { label: "Funds", active: false },
                { label: "Futures", active: false },
                { label: "Forex", active: false },
                { label: "Indices", active: false },
                { label: "Bonds", active: false },
            ],
            data: []
        }
    },
    props: {
        isOpen: Boolean,
    },
    methods: {
        onClose() {
            this.$emit('close', this.isOpen);
        },
        onSelect() {

        },
        onChipClick(label) {
            // Handle chip click
        },
        async fetchWatchlist() {
            await fetch(`http://13.127.102.151:8000/coin-api/list-of-coin/`, {
                method: "GET",
            })
                .then((res) => res.json())
                .then((data) => {
                    this.data = data.data.coins
                })
                .catch((e) => console.log(e));
            this.isProgress = false;
        },
    },
    created() {
        this.fetchWatchlist();
    }
};
</script>
