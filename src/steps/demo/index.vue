<script setup lang="ts">
import { ref } from 'vue';
import { useTranslate } from '@demo/use-translate';

const t = useTranslate({
  'zh-CN': {
    nextStep: '下一步',
    step1: '买家下单',
    step2: '商家接单',
    step3: '买家提货',
    step4: '交易完成',
    title2: '描述信息',
    title3: '竖向步骤条',
    status1: '【城市】物流状态1',
    status2: '【城市】物流状态',
    status3: '快件已发货',
    customStyle: '自定义样式',
  },
  'en-US': {
    nextStep: 'Next Step',
    step1: 'Step1',
    step2: 'Step2',
    step3: 'Step3',
    step4: 'Step4',
    title2: 'Description',
    title3: 'Vertical Steps',
    status1: '【City】Status1',
    status2: '【City】Status2',
    status3: '【City】Status3',
    customStyle: 'Custom Style',
  },
});

const active = ref(1);

const nextStep = () => {
  active.value = ++active.value % 4;
};
</script>

<template>
  <demo-block :title="t('basicUsage')">
    <van-steps :active="active">
      <van-step>{{ t('step1') }}</van-step>
      <van-step>{{ t('step2') }}</van-step>
      <van-step>{{ t('step3') }}</van-step>
      <van-step>{{ t('step4') }}</van-step>
    </van-steps>

    <van-button @click="nextStep">{{ t('nextStep') }}</van-button>
  </demo-block>

  <demo-block :title="t('customStyle')">
    <van-steps
      :active="active"
      active-icon="success"
      inactive-icon="arrow"
      active-color="#38f"
    >
      <van-step>{{ t('step1') }}</van-step>
      <van-step>{{ t('step2') }}</van-step>
      <van-step>{{ t('step3') }}</van-step>
      <van-step>{{ t('step4') }}</van-step>
    </van-steps>
  </demo-block>

  <demo-block :title="t('title3')">
    <van-steps :active="0" direction="vertical">
      <van-step>
        <h3>{{ t('status1') }}</h3>
        <p>2016-07-12 12:40</p>
      </van-step>
      <van-step>
        <h3>{{ t('status2') }}</h3>
        <p>2016-07-11 10:00</p>
      </van-step>
      <van-step>
        <h3>{{ t('status3') }}</h3>
        <p>2016-07-10 09:30</p>
      </van-step>
    </van-steps>
  </demo-block>
</template>

<style lang="less">
.demo-steps {
  .steps-success,
  .van-icon-location {
    color: var(--van-green);
  }

  .van-button {
    margin: var(--van-padding-md) 0 0 var(--van-padding-md);
  }

  p,
  h3 {
    margin: 0;
    font-weight: normal;
    font-size: inherit;
  }

  .van-steps__message + p {
    margin-bottom: 10px;
  }
}
</style>
