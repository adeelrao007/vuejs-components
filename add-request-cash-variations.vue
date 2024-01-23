<template>
  <div>
    <b-row>
      <b-col lg="4" offset="4" class="text-center">
        <CashAdd
          v-if="!showAdded"
          :cash="value"
          :type="type"
          @typeChanged="handleTypeChanged"
          @updateAmount="handleAmountUpdateChange"
          @confirm="showAdded = true" />
      </b-col>
    </b-row>
    <b-row>
      <b-col lg="4" offset="4" class="text-center">
        <CashAdded
          v-if="showAdded"
          :cash="value"
          :type="type"
          isMine
          size="xxl"
          @editCash="showAdded = false"  />
      </b-col>
    </b-row>
      <b-row>
        <b-col lg="4" offset="4" class="text-center">
          <CashAdd
            v-if="!showAdded"
            :cash="value"
            :type="type"
            @typeChanged="handleTypeChanged"
            @updateAmount="handleAmountUpdateChange"
            @confirm="showAdded = true" />
        </b-col>
      </b-row>
      <b-row>
        <b-col lg="4" offset="4" class="text-center">
          <CashAdded
            v-if="showAdded"
            :cash="value"
            :type="type"
            size="xxl"
            @editCash="showAdded = false"  />
        </b-col>
      </b-row>
  </div>
</template>

<script>
import CashAdd from '~/components/common-v2/Composites/Cash/Add'
import CashAdded from '~/components/common-v2/Composites/Cash/Added'
export default {
  name: 'AddRequestCashVariations',
  components: {
    CashAdd,
    CashAdded
  },
  data() {
    return {
      type: 'Add',
      value: 0,
      showAdded: false
    }
  },
  methods: {
    handleTypeChanged(type) {
      this.type = type
    },
    handleAmountUpdateChange(amount) {
      this.value = amount
    }
  }
}
</script>
