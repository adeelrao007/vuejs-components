<template>
  <component
    :is="dynamic"
    v-if="dynamic"
    :role="button ? 'button': 'graphics-symbol'"
    :width="width"
    :height="height"
    :fill="variant"
    :class="[variant ? `text-${variant}` : '']"
    @click="handleClickEvent"
  />
</template>

<script>
export default {
  name: 'Icon',
  props: {
    variant: {
      type: String,
      default: null,
    },
    icon: {
      type: String,
      default: 'plus',
    },
    iconDisabled: {
      type: String,
      default: null,
    },
    width: {
      type: [Number, String],
      default: 18,
    },
    height: {
      type: [Number, String],
      default: 18,
    },
    disabled: {
      type: Boolean,
      default: false,
    },
    button: {
      type: Boolean,
      default: false,
    }
  },
  computed: {
    dynamic(vm) {
      if (vm.disabled) {
        return require(`~/assets/icons/common-v2/icon-${vm.iconDisabled}.svg?inline`)
      }

      return require(`~/assets/icons/common-v2/icon-${vm.icon}.svg?inline`)
    },
  },
  methods: {
    handleClickEvent() {
      if (this.button) {
        this.$emit('click')
      }
    },
  },
}
</script>
