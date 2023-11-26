<template>
  <div class="table-auto w-full h-[60vh]">
    <table class="w-full">
      <thead class="sticky top-0 bg-dapp-black-2 justify-between">
        <tr class="text-dapp-gray-1">
          <th
            class="font-normal p-3 text-sm text-left"
            v-for="heading in headings"
          >
            {{ heading.label }}
          </th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in data" class="text-white">
          <td
            v-for="heading in headings"
            class="py-3 px-3 bg-dapp-black-3 rounded-l-md rounded-r-md border-b-[10px] border-b-dapp-black-2 text-sm"
          >
            <!-- <CoinIconLabel v-if="heading.key === 'name'" :icon="item[heading.key].icon"
                            :label="item[heading.key].base_currency_name" /> -->
            <CoinIconLabel
              v-if="heading.key === 'name'"
              icon="logos:bitcoin"
              :label="item.base_currency_symbol"
            />
            <!-- <ActionIndicator v-else-if="heading.key === 'action'" :isRise="item[heading.key].props.isRise"
                            :percent="item[heading.key].props.percent" :label="item[heading.key].props.label" /> -->
            <ActionIndicator
              v-else-if="heading.key === 'action'"
              :isRise="item.active"
              :percent="35"
              label="Buy"
            />
            <!-- <template v-else>{{ item[heading.key] }}</template> -->
            <template v-else>35%</template>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import { Icon } from "@iconify/vue2";
import CoinIconLabel from "../others/CoinIconLabel.vue";
import ActionIndicator from "./ActionIndicator.vue";
import RadialProgressBar from "vue-radial-progress";

export default {
  name: "ProgressSpinnerIndeterminate",
  components: {
    CoinIconLabel,
    Icon,
    ActionIndicator,
    RadialProgressBar,
  },
  data() {
    return {
      headings: [
        { label: "Name", key: "name" },
        { label: "Action", key: "action" },
        { label: "Score", key: "score" },
      ],
      data: [],
      isProgress: true,
    };
  },
  methods: {},
};
</script>

<style scoped>
.vue-pithy-progress {
  transition: width 0.5s ease-in-out;
}
</style>
