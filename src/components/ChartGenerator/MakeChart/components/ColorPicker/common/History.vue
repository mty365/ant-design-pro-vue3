<template>
  <div class="bee-colorPicker__record">
    <div class="color-list">
      <div class="color-item transparent" :class="{ 'color-item__round': round }" v-for="(v, i) in colorList" :key="i"
        @click="onClickRecord(v)">
        <div class="color-item__display" :style="{ backgroundColor: v }"></div>
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup name="History">
import { PropType } from "vue";
const props = defineProps({
  colorList: {
    type: Array as PropType<string[]>,
    default: () => {
      return [];
    }
  },
  round: {
    type: Boolean,
    default: true
  }
})
const emit = defineEmits(["change"])
const onClickRecord = (color: string) => {
  emit("change", color);
};
</script>

<style lang="less" scoped>
.bee-colorPicker__record {
  display: flex;
  align-items: center;
  margin-top: 20px;

  .text {
    width: 48px;
    margin-right: 10px;
    text-align: right;
    font-size: 12px;
    color: #666;
  }

  .color-list {
    width: auto;
    display: flex;
    position: relative;
    margin: 0;

    .color-item {
      position: relative;
      width: 25px;
      height: 25px;
      cursor: pointer;
      overflow: hidden;
      display: inline-block;
      vertical-align: middle;
      margin-right: 1px;
      box-shadow: 3px 0 5px rgba(0, 0, 0, 0.08);

      &__round {
        border-radius: 50%;
      }

      &.transparent {
        background-image: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAwAAAAMCAIAAADZF8uwAAAAGUlEQVQYV2M4gwH+YwCGIasIUwhT25BVBADtzYNYrHvv4gAAAABJRU5ErkJggg==);
        background-repeat: repeat;
      }

      &:hover {
        transform: scale(1.2);
        z-index: 299;
        transition: transform 0.2s;
      }

      &__display {
        width: 100%;
        height: 100%;
      }
    }
  }
}
</style>
