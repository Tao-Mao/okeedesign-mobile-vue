<template>
  <div class="demo steps">
    <o-header fixed @click-left="$router.back()">
      <div>{{ t('name') }}</div>
    </o-header>

    <demo-cell :title="t('basic')" :title-style="titleStyle">
      <o-cell>
        <o-steps :current="current" @change="handleClick">
          <o-step v-for="item in steps" :key="item.title" v-bind="item"></o-step>
        </o-steps>
      </o-cell>
    </demo-cell>

    <demo-cell :title="t('title')" :title-style="titleStyle">
      <o-cell>
        <o-steps :current="current" @change="handleClick" labelDirection="vertical">
          <o-step v-for="item in steps" :key="item.title" v-bind="item"></o-step>
        </o-steps>
      </o-cell>
    </demo-cell>

    <demo-cell :title="t('vertical1')" :title-style="titleStyle">
      <o-cell>
        <div class="steps-vertical-layout">
          <o-steps
            style="height: 300px; margin-right: 100px"
            direction="vertical"
            :current="current"
            @change="handleClick"
          >
            <o-step v-for="item in steps" :key="item.title" v-bind="item"></o-step>
          </o-steps>
        </div>
      </o-cell>
    </demo-cell>
  </div>
</template>

<script>
import demoCell from '../../../../docs/site/components/DomeCell.vue';
export default {
  data() {
    return {
      current: 2,
      steps: [
        {
          title: '已完成',
        },
        {
          title: '进行中',
          inProgress: true,
        },
        {
          title: '待完成',
        },
        {
          title: '未完成',
          status: 'error',
        },
      ],
      titleStyle: {
        'padding-left': '0.8rem',
      },
      steps2: [
        {
          title: '物流状态A',
        },
        {
          title: '物流状态B',
          inProgress: true,
        },
        {
          title: '快递已发货',
        },
      ],
    };
  },

  i18n: {
    'zh-CN': {
      name: '步骤条',
      horizontal: '水平版',
      vertical1: '竖向步骤条1',
      vertical2: '竖向步骤条2',
      basic: '基础用法',
      title: '标题在下',
    },
    'en-US': {
      name: 'Steps',
      horizontal: 'horizontal',
      basic: 'Basic Usage',
      title: 'Bottom Title',
      vertical1: 'Vertical1',
      vertical2: 'Vertical2',
    },
  },
  components: {
    demoCell,
  },
  methods: {
    handleClick(index) {
      console.log(index);
      this.current = index;
    },
  },
};
</script>

<style lang="less" scoped>
.steps {
  .steps-vertical-layout {
    display: flex;
  }
}
.demo {
  padding: 0;
}
</style>
