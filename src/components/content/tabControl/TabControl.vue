<template>
  <div class="tab-control">
    <div
      v-for="(item,index) in titles"
      :key="index"
      class="tab-control-item"
      @click="activeClick(index)"
      :class="{active:index==currentIndex}"
    >
      <span>{{item}}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "TabControl",
  data() {
    return {
      currentIndex: 0
    };
  },
  props: {
    titles: {
      type: Array,
      default() {
        return [];
      }
    }
  },
  mounted() {
    // this.getoffsetHeight();
  },
  methods: {
    activeClick(index) {
      this.currentIndex = index;
      this.$emit("tabclick", index);
      this.getoffsetHeight();
    }
  }
};
</script>

<style scoped>
.tab-control {
  display: flex;
  text-align: center;
}
.tab-control-item {
  flex: 1;
  height: 40px;
  line-height: 40px;
}
.tab-control-item span {
  padding: 5px 10px;
}
.active {
  color: pink;
}
.active span {
  border-bottom: 3px solid hotpink;
}
</style>
