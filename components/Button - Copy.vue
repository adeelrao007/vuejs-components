<template>
  <b-button
    :class="{
      'btn-shadow' : shadow,
    }"
    :size="size"
    :variant="variant"
    :pill="pill"
    :rounded="rounded"
    :block="block"
    :squared="squared"
    v-bind="$attrs"
    v-on="$listeners"
  >
    <slot>{{ label }}</slot>
  </b-button>
</template>

<script>
export default {
  name: 'Button',
  props: {
    label: {
      type: String,
      default: '',
    },
    variant: {
      type: String,
      default: 'primary',
    },
    size: {
      type: String,
      default: 'md',
      validator(variant) {
        return ['xs', 'sm', 'md', 'lg', 'xl'].includes(variant)
      },
    },
    pill: {
      type: Boolean,
      default: false,
    },
    rounded: {
      type: Boolean,
      default: false,
    },
    block: {
      type: Boolean,
      default: false,
    },
    squared: {
      type: Boolean,
      default: false,
    },
    shadow: {
      type: Boolean,
      default: false
    }
  }
}
</script>
