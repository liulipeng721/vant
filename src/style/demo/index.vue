<script setup lang="ts">
import { ref } from 'vue';
import { useTranslate } from '@demo/use-translate';

const t = useTranslate({
  'zh-CN': {
    hairline: '1px 边框',
    ellipsis: '文字省略',
    animation: '动画',
    toggle: '切换动画',
    text1: '这是一段最多显示一行的文字，后面的内容会省略',
    text2:
      '这是一段最多显示两行的文字，后面的内容会省略。这是一段最多显示两行的文字，后面的内容会省略',
  },
  'en-US': {
    hairline: 'Hairline',
    ellipsis: 'Text Ellipsis',
    animation: 'Animation',
    toggle: 'Switch animation',
    text1:
      'This is a paragraph that displays up to one line of text, and the rest of the text will be omitted.',
    text2:
      'This is a paragraph that displays up to two lines of text, and the rest of the text will be omitted.',
  },
});

const show = ref(false);
const transitionName = ref('');

const animate = (newName: string) => {
  show.value = true;
  transitionName.value = newName;

  setTimeout(() => {
    show.value = false;
  }, 500);
};
</script>

<template>
  <demo-block :title="t('ellipsis')">
    <div class="van-ellipsis">{{ t('text1') }}</div>
    <div class="van-multi-ellipsis--l2">{{ t('text2') }}</div>
  </demo-block>

  <demo-block card :title="t('hairline')">
    <div class="van-hairline--top" />
  </demo-block>

  <demo-block card :title="t('animation')">
    <van-cell is-link title="Fade" @click="animate('van-fade')" />
    <van-cell is-link title="Slide Up" @click="animate('van-slide-up')" />
    <van-cell is-link title="Slide Down" @click="animate('van-slide-down')" />
    <van-cell is-link title="Slide Left" @click="animate('van-slide-left')" />
    <van-cell is-link title="Slide Right" @click="animate('van-slide-right')" />
  </demo-block>

  <transition :name="transitionName">
    <div v-show="show" class="demo-animate-block" />
  </transition>
</template>

<style lang="less">
.demo-style {
  .van-ellipsis,
  .van-multi-ellipsis--l2 {
    max-width: 300px;
    margin-left: var(--van-padding-md);
    font-size: 14px;
    line-height: 18px;
  }

  .van-ellipsis {
    margin-bottom: var(--van-padding-md);
  }

  .van-hairline--top {
    height: 30px;
    background-color: var(--van-white);

    &::after {
      top: 5px;
    }
  }

  .demo-animate-block {
    position: fixed;
    top: 50%;
    left: 50%;
    width: 100px;
    height: 100px;
    margin: -50px 0 0 -50px;
    background-color: var(--van-blue);
    border-radius: 8px;
  }
}
</style>
