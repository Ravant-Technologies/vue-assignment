<template>
    <div>
        <div name="modal-fade" appear class="fixed inset-0 z-50 flex items-center justify-center">
            <div id="modal" name="modal-slide" appear>
                <div class="fixed inset-0 overflow-y-auto">
                    <div class="flex min-h-full items-center justify-center p-4 text-center">
                        <slot></slot>
                    </div>
                </div>
            </div>
            <div class="fixed inset-0 bg-black bg-opacity-80" @click="onClose" />
        </div>
    </div>
</template>

<script>
export default {

    props: {
        isOpen: Boolean,
        // onClose: Function,
    },
    methods: {
        onClose() {
            
        }
    }
};
</script>

<style scoped>
.modal-fade-enter-active,
.modal-fade-leave-active {
    transition: opacity 0.3s ease;
}

.modal-fade-enter,
.modal-fade-leave-to {
    opacity: 0;
}

.modal-slide-enter-active,
.modal-slide-leave-active {
    transition: transform 0.3s ease;
}

.modal-slide-enter,
.modal-slide-leave-to {
    transform: translateY(-20px);
}
</style>
