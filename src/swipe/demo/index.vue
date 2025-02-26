<script setup lang="ts">
import { useTranslate } from '@demo/use-translate';
import { Toast } from '../../toast';

const t = useTranslate({
  'zh-CN': {
    title2: '懒加载',
    title3: '监听 change 事件',
    title4: '纵向滚动',
    title5: '自定义滑块大小',
    title6: '自定义指示器',
    message: '当前 Swipe 索引：',
  },
  'en-US': {
    title2: 'Lazy Render',
    title3: 'Change Event',
    title4: 'Vertical Scrolling',
    title5: 'Set SwipeItem Size',
    title6: 'Custom indicator',
    message: 'Current Swipe index:',
  },
});

const images = [
  'https://img.yzcdn.cn/vant/apple-1.jpg',
  'https://img.yzcdn.cn/vant/apple-2.jpg',
  'https://img.yzcdn.cn/vant/apple-3.jpg',
  'https://img.yzcdn.cn/vant/apple-4.jpg',
];

const onChange = (index: number) => Toast(t('message') + index);
</script>

<template>
  <demo-block :title="t('basicUsage')">
    <van-swipe :autoplay="3000" indicator-color="white">
      <van-swipe-item>1</van-swipe-item>
      <van-swipe-item>2</van-swipe-item>
      <van-swipe-item>3</van-swipe-item>
      <van-swipe-item>4</van-swipe-item>
    </van-swipe>
  </demo-block>

  <demo-block :title="t('title2')">
    <van-swipe :autoplay="3000" lazy-render>
      <van-swipe-item v-for="image in images" :key="image">
        <img :src="image" />
      </van-swipe-item>
    </van-swipe>
  </demo-block>

  <demo-block :title="t('title3')">
    <van-swipe indicator-color="white" @change="onChange">
      <van-swipe-item>1</van-swipe-item>
      <van-swipe-item>2</van-swipe-item>
      <van-swipe-item>3</van-swipe-item>
      <van-swipe-item>4</van-swipe-item>
    </van-swipe>
  </demo-block>

  <demo-block :title="t('title4')">
    <van-swipe
      vertical
      :autoplay="3000"
      indicator-color="white"
      style="height: 200px"
      class="demo-swipe--vertical"
    >
      <van-swipe-item>1</van-swipe-item>
      <van-swipe-item>2</van-swipe-item>
      <van-swipe-item>3</van-swipe-item>
      <van-swipe-item>4</van-swipe-item>
    </van-swipe>
  </demo-block>

  <demo-block :title="t('title5')">
    <van-swipe :width="300" :loop="false" indicator-color="white">
      <van-swipe-item>1</van-swipe-item>
      <van-swipe-item>2</van-swipe-item>
      <van-swipe-item>3</van-swipe-item>
      <van-swipe-item>4</van-swipe-item>
    </van-swipe>
  </demo-block>

  <demo-block :title="t('title6')">
    <van-swipe>
      <van-swipe-item>1</van-swipe-item>
      <van-swipe-item>2</van-swipe-item>
      <van-swipe-item>3</van-swipe-item>
      <van-swipe-item>4</van-swipe-item>
      <template #indicator="{ active }">
        <div class="custom-indicator">{{ active + 1 }}/4</div>
      </template>
    </van-swipe>
  </demo-block>
</template>

<style lang="less">
.demo-swipe {
  padding-bottom: 30px;

  .van-swipe {
    &-item {
      color: var(--van-white);
      font-size: 20px;
      line-height: 150px;
      text-align: center;

      &:nth-child(even) {
        background-color: #39a9ed;
      }

      &:nth-child(odd) {
        background-color: #66c6f2;
      }
    }

    img {
      display: block;
      box-sizing: border-box;
      width: 100%;
      height: 240px;
      padding: 30px 60px;
      background-color: var(--van-white);
      pointer-events: none;
    }
  }

  &--vertical {
    .van-swipe-item {
      line-height: 200px;
    }
  }

  .custom-indicator {
    position: absolute;
    right: 5px;
    bottom: 5px;
    padding: 2px 5px;
    color: var(--van-white);
    font-size: 12px;
    background: rgba(0, 0, 0, 0.1);
  }
}
</style>
