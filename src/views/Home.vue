<template>
  <div class="h-screen overflow-y-hidden overflow-x-hidden bg-dapp-black-1">
    <Header @toggle="this.onToggle" />
    <div class="flex flex-row justify-between w-full">
      <LeftSidebar />
      <div class="flex">
        <main class="pr-2">
          <div class="flex items-start gap-2 w-90">
            <slot></slot>
            <MainDashboard />
            <CardMarketplaceModal
              v-if="isCardModalOpen"
              :isOpen="this.isCardModalOpen"
              @close="onClose"
            />
            <AddWatchlistModal
              v-if="isAddModalOpen"
              :isOpen="this.isAddModalOpen"
              @close="onClose"
            />

            <RightSidebar
              :class="!toggle ? 'hidden' : 'absolute right-2'"
              @isModalOpen="handleCardModalOpen"
            />
          </div>
        </main>
      </div>
    </div>
  </div>
</template>
<script>
import CardMarketplaceModal from "../components/RightSideBar/CardMarketplaceModal.vue";
import AddWatchlistModal from "../components/RightSideBar/AddWatchlistModal.vue";
import Header from "../components/Header/index.vue";
import RightSidebar from "../components/RightSideBar/index.vue";
import LeftSidebar from "../components/LeftSideBar/index.vue";
// import { DAppProvider } from "@usedapp/core";
import MainDashboard from "../components/MainDashboard/index.vue";

export default {
  components: {
    Header,
    RightSidebar,
    LeftSidebar,
    MainDashboard,
    CardMarketplaceModal,
    AddWatchlistModal,
  },
  name: "Home",
  data() {
    return {
      toggle: false,
      rightSideState: false,
      isCardModalOpen: false,
      isAddModalOpen: false,
      isOpenState: false,
    };
  },
  mounted() {
    window.addEventListener("resize", this.onResize);
    window.addEventListener("click", this.handleWindowClick);
  },
  beforeDestroy() {
    window.removeEventListener("resize", this.onResize);
    window.removeEventListener("click", this.handleWindowClick);
  },
  methods: {
    onToggle(value) {
      this.rightSideState = value;
      if (this.rightSideState) {
        if (window.innerWidth < 1280) {
          this.toggle = true;
        } else {
          this.toggle = false;
        }
      } else {
        this.toggle = false;
      }
    },
    onResize() {
      if (this.rightSideState) {
        if (window.innerWidth < 1280) {
          this.toggle = true;
        } else {
          this.toggle = false;
        }
      } else {
        this.toggle = false;
      }
    },
    handleCardModalOpen(value) {
      if (value == "card") {
        this.isCardModalOpen = true;
        this.isAddModalOpen = false;
      } else {
        this.isAddModalOpen = true;
        this.isCardModalOpen = false;
      }
    },
    onClose(value) {
      this.isAddModalOpen = !value;
      this.isCardModalOpen = !value;
      this.isOpenState = !value;
    },
    handleWindowClick() {
      if (this.isAddModalOpen || this.isCardModalOpen) {
        if (this.isOpenState) {
          this.isAddModalOpen = false;
          this.isCardModalOpen = false;
          this.isOpenState = false;
        } else {
          this.isOpenState = true;
        }
      }
    },
  },
};
</script>
