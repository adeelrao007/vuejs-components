<template>
  <b-card no-body class="composite-summary-card-mobile d-inline-block text-center border-0 justify-content-center flex-wrap align-content-center shadow-none">
    <b-card-header class="d-inline-block border-0 m-0 w-100">
      <div class="icon-wrapper text-center d-flex justify-content-center flex-wrap align-content-center">
        <Icon
          v-if="icon"
          :icon="icon"
          :height="iconHeight"
          :width="iconWidth"
        />
      </div>
    </b-card-header>
    <b-card-body class="m-0 p-0 d-inline-block text-center">
      <b-card-text class="heading text-capitalize d-inline-block w-auto h-auto">
        {{heading}}
      </b-card-text>
      <b-card-text v-if="rewardPoints" :class="`text-${rewardInfoVariant}`" class="sub-heading d-inline-block w-auto h-auto">
        {{rewardText.replace('{-points-}', rewardPoints)}}
      </b-card-text>
      <b-card-text v-if="information" class="information d-inline-block h-auto">
        {{information}}
      </b-card-text>
      <b-card-text v-if="anchorText" class="button">
        <b-link :class="`text-${anchorVariant}`" :href="anchorLink">{{ anchorText }}</b-link>
      </b-card-text>
    </b-card-body>
  </b-card>
</template>

<script>
import Icon from '~/components/common-v2/Icon/Icon'
export default {
  name: 'SummaryCardMobile',
  components: {
    Icon
  },
  props: {
    icon: {
      type: String,
      default: 'exchange-circle'
    },
    heading: {
      type: String,
      default: null
    },
    rewardPoints: {
      type: [String, Number],
      default: 0
    },
    rewardText: {
      type: String,
      default: null
    },
    information: {
      type: String,
      default: null
    },
    rewardInfoVariant: {
      type: String,
      default: 'primary'
    },
    anchorText: {
      type: String,
      default: null
    },
    anchorVariant: {
      type: String,
      default: 'primary'
    },
    anchorLink: {
      type: String,
      default: null
    },
    iconWidth: {
      type: [Number, String],
      default: 40,
    },
    iconHeight: {
      type: [Number, String],
      default: 40,
    },
  },
}
</script>
