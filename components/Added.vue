<template>
  <div>
    <span
      class="w-100 bg-white p3 py-2"
      :class="{
        'fw-normal': size === 'xxl',
        'fw-medium': size === 'xs'
      }">
      <Icon
        icon="dollar"
        variant="black"
        :width="(size === 'xxl' ? 16 : 12)"
        :height="(size === 'xxl' ? 16 : 12)" />
      <span class="fw-semibold">
        {{ $t('common.' + (isMine ? 'you' : 'they')) }}
      </span> {{ $t('common.' + (type === $t('trades.trade_arena.add') ? 'added' : 'requested')) }}
      <span class="fw-semibold">
        {{ getFormattedPrice(cash) }}
      </span> {{ $t('common.on_top') }}
      <span class="ml-2">
        <Icon
          icon="info-circle-fill"
          variant="primary"
          :width="(size === 'xxl' ? 16 : 12)"
          :height="(size === 'xxl' ? 16 : 12)" />
      </span>
    </span>
    <div v-if="allowEdit">
      <span
        role="button"
        class="text-info-800 p3"
        @click="$emit('editCash')">
        {{ $t('trades.trade_arena.edit_cash') }}
      </span>
    </div>
  </div>
</template>
<script>
import Icon from '~/components/common-v2/Icon/Icon'
export default {
  name: 'Added',
  components: {
    Icon
  },
  props: {
    size: {
      type: String,
      default: 'xxl',
      validator(size) {
        return ['xs', 'xxl'].includes(size)
      }
    },
    type: {
      type: String,
      default: '',
    },
    isMine: {
      type: Boolean,
      default: false,
    },
    cash: {
      type: Number,
      default: 0,
    },
    allowEdit: {
      type: Boolean,
      default: false,
    },
  },
  methods: {
    getFormattedPrice(price) {
      return this.$root.$options.filters.toCurrency(price)
    },
  }
}
</script>
