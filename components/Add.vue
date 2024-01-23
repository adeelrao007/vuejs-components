<template>
  <div>
    <SelectLinks
      :options="types"
      :selected="type"
      class="mb-2"
      size="xs"
      @optionSelected="handleTypeChanged" />
      <div>
        <ValidationObserver v-slot="{ valid }">
          <FormInput
            :value="cash"
            :rules="{ required: true, numeric: true, min_value: 0 }"
            :name="$t('trades.trade_arena.number')"
            :placeholder="$t('trades.trade_arena.enter_amount')"
            iconPrepend="dollar"
            iconPrependVariant="black"
            borderVariant="light-400"
            size="md"
            class="mr-5 text-left"
            @input="handleInputChange" />
          <Button
            :disabled="!valid"
            :label="$t('trades.trade_arena.confirm')"
            class="p2 fw-medium text-white"
            variant="primary"
            size="md"
            block
            pill
            @click="$emit('confirm')" />
        </ValidationObserver>
      </div>
  </div>
</template>
<script>
import { ValidationObserver } from 'vee-validate'
import SelectLinks from '~/components/common-v2/Composites/SelectLinks'
import Button from '~/components/common-v2/Button'
import FormInput from '~/components/common-v2/Form/FormInput'
export default {
  name: 'Add',
  components: {
    SelectLinks,
    Button,
    FormInput,
    ValidationObserver
  },
  props: {
    cash: {
      type: Number,
      default: 0,
    },
    type: {
      type: String,
      default: '',
    },
  },
  data() {
    return {
      types: [
        {
          'key': this.$t('trades.trade_arena.add'),
          'label': this.$t('trades.trade_arena.add_cash'),
        },
        {
          'key': this.$t('trades.trade_arena.request'),
          'label': this.$t('trades.trade_arena.request_cash'),
        }
      ],
    }
  },
  methods: {
    handleTypeChanged(selectedType) {
      this.$emit('typeChanged', selectedType)
    },
    handleInputChange(value) {
      this.$emit('updateAmount', value)
    }
  },
}
</script>
