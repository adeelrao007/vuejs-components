<template>
  <b-row class="list-table">
    <b-col md="12">
      <b-row class="table-header">
        <b-col md="4" class="text-left">
          <label class="title p2 fw-bold pl-3">
            <span>{{ $tc('common.product', 0) }}</span>
            <Icon button icon="chevron-down-fill" width="8" height="8" class="sort-icon" :class="{
              'desc': isDescending('product')
            }" @click="sortBy('product')" />
          </label>
        </b-col>
        <b-col md="6" class="p-0">
          <b-row class="no-gutters align-items-center">
            <b-col md="2" class="text-center">
              <label class="title p2 fw-bold">
                <span>{{ $t('common.qty') }}</span>
                <Icon button icon="chevron-down-fill" width="8" height="8" class="sort-icon" :class="{
                  'desc': isDescending('quantity')
                }" @click="sortBy('quantity')" />
              </label>
            </b-col>
            <b-col md="3" class="text-center">
              <label class="title p2 fw-bold">
                <span>{{ $t('common.min_offer') }}</span>
                <Icon button icon="chevron-down-fill" width="8" height="8" class="sort-icon" :class="{
                  'desc': isDescending('min_offer')
                }" @click="sortBy('min_offer')" />
              </label>
            </b-col>
            <b-col md="3" class="text-center">
              <label class="title p2 fw-bold">
                <span>{{ $t('common.price') }}</span>
                <Icon button icon="chevron-down-fill" width="8" height="8" class="sort-icon" :class="{
                  'desc': isDescending('price')
                }" @click="sortBy('price')" />
              </label>
            </b-col>
            <b-col md="4" class="text-center">
              <label class="title p2 fw-bold">
                <span>{{ $t('common.updated') }}</span>
                <Icon button icon="chevron-down-fill" width="8" height="8" class="sort-icon" :class="{
                  'desc': isDescending('last_updated')
                }" @click="sortBy('last_updated')" />
              </label>
            </b-col>
          </b-row>
        </b-col>
        <b-col md="2" class="text-center">
          <label class="title p2 fw-bold">
            {{ $t('common.actions') }}
          </label>
        </b-col>
      </b-row>
    </b-col>
    <b-col v-for="(listItem, index) in draftsList" :key="`table-product-${index}`" md="12">
      <b-row class="table-content align-items-center">
        <b-col v-if="listItem.items.length === 1" md="4">
          <ProductDetailStack :img-src="getProductImage(listItem.items[0].product)"
            :title="listItem.items[0].product.name" :sub-line1="`${$t('common.sku')}: ${listItem.items[0].product.sku}`"
            :sub-line2="`${$t('common.colorway')}: ${listItem.items[0].product.colorway}, ${$tc('common.size', 0)}: ${listItem.items[0].size.size}`"
            :sub-line3="`${$t('common.box_condition')}: ${listItem.items[0].packaging_condition.name}`" />
        </b-col>
        <b-col v-else-if="listItem.items.length > 1" md="4">
          <div class="multiple-products-wrapper pl-6 d-flex justify-content-start align-items-center">
            <b-row class="icon-wrapper d-inline-block">
              <b-col cols="12">
                <Icon variant="light-600" icon="stack-list" width="64" height="64" class="d-inline-block" />
              </b-col>
            </b-row>
            <b-col cols="12" class="info-wrapper">
              <span class="ml-5 mr-5 fw-semibold p3">
                {{ $t('common.multi_products') }} ({{ $t('common.n_items', {n: listItem.items.length}) }})
              </span>
              <Icon v-if="activeProductList !== index" button icon="chevron-down-slim" width="16" height="16"
                @click="activeProductList = index" />
              <Icon v-else-if="activeProductList === index" button icon="chevron-up-slim" width="16" height="16"
                @click="activeProductList = null" />
            </b-col>
          </div>
        </b-col>
        <b-col md="6" class="p-0">
          <b-row class="no-gutters align-items-center">
            <b-col md="2" class="text-center">
              {{ (listItem.quantity) ? listItem.quantity : '&#8211;' }}
            </b-col>
            <b-col md="3" class="text-center">
              {{ listItem.min_offer | toCurrency }}
            </b-col>
            <b-col md="3" class="text-center">
              {{ listItem.price | toCurrency }}
            </b-col>
            <b-col md="4" class="text-center">
              {{ listItem.created_at | formatDate('DD/MM/YYYY') }}
            </b-col>
          </b-row>
        </b-col>
        <b-col md="2" class="d-flex justify-content-center">
          <Button variant="alt-info-100" class="mr-3" size="md" @click="$emit('edit', listItem)">
            <Icon icon="pencil" class="text-alt-info-800" />
          </Button>
          <Button variant="danger-100" size="md" @click="$emit('delete', listItem)">
            <Icon icon="trash" class="text-danger-600" />
          </Button>
        </b-col>
        <b-col v-if="listItem.items.length > 1" md="12" :class="[
          activeProductList === index && 'd-block',
          activeProductList !== index && 'd-none',
        ]">
          <b-row>
            <b-col v-for="(item, pIndex) in listItem.items" :key="`product-item-${pIndex}`" md="3"
              :offset="(pIndex === 0 ? 2 : 0)">
              <ProductDetailStack size="sm" imgWrapperClass="d-flex align-items-center"
                :img-src="getProductImage(item.product)">
                <template #sub-line-1>
                  <div class="sub-line fw-semibold text-dark">{{ item.product.name }}</div>
                </template>
              </ProductDetailStack>
            </b-col>
          </b-row>
        </b-col>
      </b-row>
    </b-col>
  </b-row>
</template>

<script>
import Icon from '~/components/common-v2/Icon/Icon'
import Button from '~/components/common-v2/Button'
import ProductDetailStack from '~/components/common-v2/Composites/ProductDetailStack'
export default {
  name: 'CsvDraft',
  components: {
    Icon,
    Button,
    ProductDetailStack
  },
  props: {
    draftsList: {
      type: Array,
      default: () => [],
    },
  },
  data() {
    return {
      activeProductList: null,
      orderByField: 'product',
      orderByDirection: 'asc',
    }
  },
  methods: {
    getProductImage(product) {
      return this.$root.$options.filters.getProductImageUrl(product)
    },
    sortBy(column) {
      if (this.orderByField === column) {
        this.orderByDirection = (this.orderByDirection === 'asc') ? 'desc' : 'asc'
      } else {
        this.orderByDirection = 'asc'
      }
      this.orderByField = column
      this.$emit('sort', {
        orderByField: this.orderByField,
        orderByDirection: this.orderByDirection,
      })
    },
    isDescending(column) {
      return (this.orderByField === column && this.orderByDirection === 'desc')
    }
  },
}
</script>
