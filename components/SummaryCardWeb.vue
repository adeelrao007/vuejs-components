<template>
  <b-card no-body class="composite-summary-card-web d-inline-block text-center position-relative">
    <b-card-header class="d-inline-block border-0 m-0 p-0 w-100">
      <div class="icon-wrapper text-center d-flex">
        <Icon :icon="icon" width="120" height="120" />
      </div>
    </b-card-header>
    <b-card-body class="m-0 p-0 d-inline-block text-left w-100">
      <b-card-text class="heading text-capitalize w-auto h-auto m-0">
        {{heading}}
      </b-card-text>
      <b-card-text :class="`text-${subHeadingVariant}`" class="sub-heading text-capitalize w-auto h-auto">
        {{subHeading}}
      </b-card-text>
      <b-card-text class="information">
        <div v-html="getInformation()"></div>
      </b-card-text>
      <b-card-text class="button d-flex position-absolute">
        <Button v-if="buttonText1" :label="buttonText1" class="btn-light text-primary p-0 mr-2" size="xs" @click="$router.push(buttonLink1)"  />
        <Button v-if="buttonText2" :label="buttonText2" class="btn-light text-primary p-0" size="xs" @click="$router.push(buttonLink2)"/>
      </b-card-text>
    </b-card-body>
  </b-card>
</template>

<script>
import Button from '~/components/common-v2/Button'
import Icon from '~/components/common-v2/Icon/Icon';
export default {
  name: 'SummaryCardWeb',
  components: {
    Button,
    Icon
  },
  props: {
    icon: {
      type: String,
      default: 'exchange-shoe-shirt'
    },
    heading: {
      type: String,
      default: null
    },
    subHeading: {
      type: String,
      default: null
    },
    subHeadingVariant: {
      type: String,
      default: 'primary'
    },
    information: {
      type: String,
      default: ''
    },
    rewardPoints: {
      type: [Number, String],
      default: 0
    },
    buttonText1: {
      type: String,
      default: null
    },
    buttonLink1: {
      type: String,
      default: null
    },
    buttonText2: {
      type: String,
      default: null
    },
    buttonLink2: {
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
  methods: {
    getInformation(){
      return this.information.replace('{-points-}', `<span class='text-primary fw-semibold'>${this.rewardPoints} Points</span>`)
    }
  },
}
</script>
