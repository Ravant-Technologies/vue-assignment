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
                    <h2 class="text-xl lg:text-2xl 2xl:text-3xl font-medium leading-[1.2] text-white">Cards Marketplace</h2>
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
                        <transition-group class="mt-7 grid grid-cols-1 lg:grid-cols-2 xl:grid-cols-3 gap-3 md:gap-5 ">
                            <Card key='1' label="Ghost Patterns" active="true" description="By Wolf Trade" value="" />
                            <Card key='2' label="Ghost Patterns" description="Ghost Patterns" value="" @select="onSelect" />
                            <Card key='3' label="Ghost Patterns" description="Ghost Patterns" value="" @select="onSelect" />
                            <Card key='4' label="Ghost Patterns" description="Ghost Patterns" value="" @select="onSelect" />
                            <Card key='5' label="Ghost Patterns" description="Ghost Patterns" value="" @select="onSelect" />
                            <Card key='6' label="Ghost Patterns" description="Ghost Patterns" value="" @select="onSelect" />
                            <Card key='7' label="Ghost Patterns" description="Ghost Patterns" value="" @select="onSelect" />
                            <Card key='8' label="Ghost Patterns" description="Ghost Patterns" value="" @select="onSelect" />
                            <Card key='9' label="Ghost Patterns" description="Ghost Patterns" value="" @select="onSelect" />
                        </transition-group>
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

export default {
    components: {
        Modal,
        Card,
        Icon
    },
    props: {
        isOpen: Boolean,
    },
    data() {
        return {
            data: []
        }
    },
    methods: {
        onClose() {
            this.$emit('close', this.isOpen);
        },
        onSelect() {

        },
        // async fetchWatchlist() {
        //     await fetch(`http://13.127.102.151:8000/coin-api/list-of-coin/`, {
        //         method: "GET",
        //     })
        //         .then((res) => res.json())
        //         .then((data) => {
        //             this.data = data.results
        //         })
        //         .catch((e) => console.log(e));
        //     this.isProgress = false;
        // },
    },
    created() {
        this.fetchWatchlist();
    }
    // async mounted() {
    //     try {
    //         const response = await axios.get(`http://13.127.102.151:8000/coin-api/list-of-coin/`);
    //         console.log(response);
    //         this.data = response.data.results;
    //         console.log(this.data)
    //     } catch (error) {
    //         console.error('Error fetching posts:', error);
    //     }
    // },
};
</script>
