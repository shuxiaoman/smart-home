<template>
  <div>
    <div class="flex" style="justify-content: space-between;padding: 20px">
      <div class="hello-text">
        Good Morning , Grain Full
      </div>
      <grain-full-button type="circular" width="30px" style="margin-right: 5px">
        <i class="upper-right-button"></i>
      </grain-full-button>
    </div>
    <div class="scroll-panel">
      <grain-full-panel
        v-for="(item, index) in statusList"
        :key="index"
        :active="statusActiveIndex === index"
        @click.native="clickPanel(index)"
        icon="#icon-guizi-"
        style="margin: 15px 0 15px 30px;"
      >
        <grain-full-icon :name="item.icon" />
        <p style="margin:0 0 0 5px;font-size: 13px;font-weight: 500">
          {{ item.name }}
        </p>
      </grain-full-panel>
      <!--防止右边margin无效-->
      <div><div style="height: 1px;width: 10px"></div></div>
    </div>
    <grain-full-tab
      v-model="tabBarIndex"
      :tags-scroll="true"
      :lazy-render="false"
      style="margin-top: 20px"
    >
      <grain-full-tab-item name="Usual">
        <usual />
      </grain-full-tab-item>
      <grain-full-tab-item name="LivingRoom">
        <living-room />
      </grain-full-tab-item>
      <grain-full-tab-item name="BedRoom">
        <bed-room />
      </grain-full-tab-item>
      <grain-full-tab-item name="BathRoom">
        <bath-room />
      </grain-full-tab-item>
    </grain-full-tab>
  </div>
</template>

<script>
import GrainFullButton from "../../components/Neumorphism/GrainFullButton";
import GrainFullPanel from "../../components/Neumorphism/GrainFullPanel";
import GrainFullTab from "../../components/Neumorphism/GrainFullTab";
import GrainFullTabItem from "../../components/Neumorphism/GrainFullTabItem";
import GrainFullIcon from "../../components/Neumorphism/GrainFullIcon";
import Usual from "../components/Usual";
import LivingRoom from "../components/LivingRoom";
import BedRoom from "../components/BedRoom";
import BathRoom from "../components/BathRoom";

export default {
  name: "HomePage",
  components: {
    BathRoom,
    BedRoom,
    LivingRoom,
    Usual,
    GrainFullIcon,
    GrainFullTabItem,
    GrainFullTab,
    GrainFullButton,
    GrainFullPanel
  },
  data() {
    return {
      tabBarIndex: 0,
      showContent: true,
      statusActiveIndex: 0,
      statusList: [
        { name: "At Home", active: false, icon: "#icon-home" },
        { name: "Going Out", active: false, icon: "#icon-go-out" },
        { name: "Sleeping", active: false, icon: "#icon-sleep" },
        { name: "Napping", active: false, icon: "#icon-chair" }
      ]
    };
  },
  mounted() {},
  methods: {
    clickPanel(index) {
      this.statusActiveIndex = index;
    }
  }
};
</script>

<style scoped lang="scss">
.flex {
  display: flex;
  align-items: center;
}
.hello-text {
  font-size: 16px;
  font-weight: bolder;
  color: #9599a6;
}
.upper-right-button {
  height: 4px;
  width: 4px;
  background-color: #b90000;
  border-radius: 2px;
}

//icon图标
.icon {
  width: 1em;
  height: 1em;
  vertical-align: -0.15em;
  fill: currentColor;
  overflow: hidden;
}

.scroll-panel {
  overflow-x: auto;
  display: flex;
  align-items: center;
  justify-content: flex-start;
  /*&::-webkit-scrollbar {*/
  /*  !*display: none;*!*/
  /*  !*width: 0;*!*/
  /*  background: transparent;*/
  /*}*/
}
</style>
