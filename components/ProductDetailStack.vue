<template>
  <b-card
    no-body
    class="product-detail-stack shadow-none border-0 m-0 bg-transparent h-auto rounded-0"
    :class="{
      'empty-view': emptyView,
      'offer-view w-auto': offerView,
      'multiple-product': multipleProduct,
      'grid-view w-100': gridView,
      'trade-wants': tradeWants
    }"
    :size="size"
  >
  <slot>
    <b-row v-if="gridView">
      <b-col cols="2">
        <div class="image-wrapper position-relative">
          <slot name="image">
            <img :src="imgSrc" class="w-100 h-100" />
          </slot>
        </div>
      </b-col>
      <b-col cols="3">
        <div class="content">
          <slot name="title">
            <a v-if="showLinkOnTitle"
               class="p2 fw-bold title text-decoration-underline cursor-pointer"
               :class="`text-${titleLinkVariant}`"
               @click="$emit('click')"
            >
              {{ title }}
            </a>
            <div v-else class="p2 fw-bold title" :class="`text-${titleVariant}`">{{ title }}</div>
          </slot>
          <slot name="sub-line-1">
            <div v-if="subLine1"
                 class="sub-line mt-1 p3 fw-medium"
                 :class="[`text-${subLineVariant}`, {'mt-2': offerView}]"
            >
              {{ subLine1 }}
            </div>
          </slot>
          <slot name="sub-line-3">
            <div
              v-if="subLine3"
              class="sub-line mt-1 p3 fw-medium"
              :class="[`text-${subLineVariant}`, {'mt-1': offerView}]"
            >
              {{ subLine3 }}
            </div>
          </slot>
          <slot name="sub-line-5">
            <div v-if="subLine5"
                 class="sub-line mt-1 p3 fw-medium"
                 :class="[`text-${subLineVariant}`, {'mt-1': offerView}]"
            >
              {{ subLine5 }}
            </div>
          </slot>
        </div>
      </b-col>
      <b-col cols="2">
        <div class="content">
          <slot name="sub-line-2">
            <div v-if="subLine2"
                 class="sub-line mt-5 p3 fw-medium"
                 :class="[`text-${subLineVariant}`, {'mt-1': offerView}]"
            >
              {{ subLine2 }}
            </div>
          </slot>
          <slot name="sub-line-4">
            <div v-if="subLine4"
                 class="sub-line mt-1 p3 fw-medium"
                 :class="[`text-${subLineVariant}`, {'mt-1': offerView}]"
            >{{ subLine4 }}</div>
          </slot>
        </div>
      </b-col>
    </b-row>
    <div v-else class="d-flex">
      <div v-if="!emptyView"
           class="image-wrapper position-relative"
           :class="[
             {'pt-5 pb-7 d-flex align-items-center justify-content-center w-100' : multipleProduct},
             {'px-3 py-5 bg-white' : offerView},
             imgWrapperClass
           ]"
      >
        <slot name="image">
          <img :src="imgSrc" class="w-100 h-100" />
          <a v-if="linkTextOnImage"
             class="p3 fw-semibold text-decoration-underline cursor-pointer position-absolute w-100 text-center"
             :class="`text-${linkTextVariant}`"
             @click="$emit('click')" >
            {{ linkTextOnImage }}
          </a>
        </slot>
      </div>
      <div class="d-flex flex-column justify-content-top content flex-grow-1"
        :class="[
          {'justify-content-center': size === 'sm' && !offerView || size === 'md'},
          {'pl-6' : !emptyView},
          contentClass
        ]"
      >
        <slot name="content">
          <slot name="title">
            <a v-if="showLinkOnTitle"
               class="p2 fw-medium title text-decoration-underline cursor-pointer"
               :class="`text-${titleLinkVariant}`"
               @click="$emit('click')"
            >
              {{ title }}
            </a>
            <div
              v-else
              class="title"
              :class="[
                `text-${titleVariant}`,
                {'fw-semibold' : size === 'sm'},
                {'p3' : offerView},
                {'p2 mb-1 fw-bold' : emptyView},
                {'p3' : size === 'sm' && !offerView},
                {'p2 fw-bold' : size === 'md'},
              ]"
            >
              {{ title }}
            </div>
          </slot>
          <slot name="sub-line-1">
            <div v-if="subLine1"
                 class="sub-line"
                 :class="[
                   `text-${subLineVariant}`,
                   {'mt-2 p4': offerView},
                   {'p4': emptyView},
                   { 'p2 fw-medium' : size === 'md' },
                   {'p3' : size === 'sm' && !offerView},
                   {'mt-1': tradeWants}
                 ]"
            >
              {{ subLine1 }}
            </div>
          </slot>
          <slot name="sub-line-2">
            <div v-if="subLine2"
                 class="sub-line"
                 :class="[
                   `text-${subLineVariant}`,
                   {'mt-1 p4': offerView},
                   {'p4': emptyView},
                   {'p2 fw-medium' : size === 'md'},
                   {'p3' : size === 'sm' && !offerView},
                   {'mt-1': tradeWants}
                 ]"
            >
              {{ subLine2 }}
            </div>
          </slot>
          <slot name="sub-line-3">
            <div
              v-if="subLine3"
              class="sub-line"
              :class="[
                   `text-${subLineVariant}`,
                   {'mt-1': offerView},
                   {'mt-1 p4': offerView},
                   {'p4': emptyView},
                   {'p2 fw-medium' : size === 'md'},
                   {'p3' : size === 'sm' && !offerView},
                    {'mt-1': tradeWants}
                 ]"
              >
              {{ subLine3 }}
            </div>
          </slot>
          <slot name="sub-line-4">
            <div v-if="subLine4"
                 class="sub-line"
                 :class="[
                   `text-${subLineVariant}`,
                   {'mt-1 p4': offerView},
                   {'p4': emptyView},
                   {'p2 fw-medium' : size === 'md' },
                   {'p3' : size === 'sm' && !offerView},
                   {'mt-1': tradeWants}
                 ]"
            >{{ subLine4 }}</div>
          </slot>
          <slot name="sub-line-5">
            <div v-if="subLine5"
                 class="sub-line"
                 :class="[
                   `text-${subLineVariant}`,
                   {'mt-1 p4': offerView},
                   {'p4': emptyView},
                   {'p2 fw-medium' : size === 'md'},
                   {'p3' : size === 'sm' && !offerView},
                   {'mt-1': tradeWants}
                 ]"
            >
              {{ subLine5 }}
            </div>
          </slot>
        </slot>
      </div>
    </div>
  </slot>
  </b-card>
</template>

<script>
export default {
  name: 'ProductDetailStack',
  props: {
    size: {
      type: String,
      default: 'md',
      validator(size) {
        return ['sm', 'md', 'lg'].includes(size)
      }
    },
    imgSrc: {
      type: String,
      default: null
    },
    title: {
      type: String,
      default: ''
    },
    titleVariant: {
      type: String,
      default: 'black'
    },
    subLineVariant: {
      type: String,
      default: 'light-700'
    },
    subLine1: {
      type: String,
      default: ''
    },
    subLine2: {
      type: String,
      default: ''
    },
    subLine3: {
      type: String,
      default: ''
    },
    subLine4: {
      type: String,
      default: ''
    },
    subLine5: {
      type: String,
      default: ''
    },
    linkTextOnImage: {
      type: String,
      default: null
    },
    linkTextVariant: {
      type: String,
      default: 'info-800'
    },
    showLinkOnTitle: {
      type: Boolean,
      default: false
    },
    titleLinkVariant: {
      type: String,
      default: 'info-800'
    },
    isMobileView: {
      type: Boolean,
      default: false
    },
    emptyView: {
      type: Boolean,
      default: false
    },
    offerView: {
      type: Boolean,
      default: false
    },
    multipleProduct: {
      type: Boolean,
      default: false
    },
    contentClass: {
      type: String,
      default: ''
    },
    gridView: {
      type: Boolean,
      default: false
    },
    tradeWants: {
      type: Boolean,
      default: false
    },
    imgWrapperClass: {
      type: String,
      default: ''
    },
  },
}
</script>
