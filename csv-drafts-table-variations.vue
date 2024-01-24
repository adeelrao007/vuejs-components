<template>
  <div>
    <CsvDraftTable :draftsList="draftsListItems" />
  </div>
</template>

<script>
import CsvDraftTable from '~/components/common-v2/Composites/Table/CsvDraft'
export default {
  name: 'CsvDraftsTableVariations',
  components: {
    CsvDraftTable
  },
  data() {
    return {
      draftsListItems: [{
        id: 12345678,
        quantity: null,
        min_offer: 165830,
        price: null,
        created_at: '2023-04-05T07:56:33.000000Z',
        items: [{
          size: {
            size: '20',
          },
          packaging_condition: {
            name: 'Excellent',
          },
          product: {
            name: 'Converse All Star Ox Red',
            colorway: 'Red',
            sku: 'M9696',
            estimated_market_value: 9900,
            image: '//images.deadstock.co/products/sneakers/M9696/800xAUTO/IMG01.jpg',
            category: {
              name: 'sneakers'
            }
          }
        },
        {
          size: {
            size: '20',
          },
          packaging_condition: {
            name: 'Excellent',
          },
          product: {
            name: 'Converse All Star Ox Red',
            colorway: 'Red',
            sku: 'M9696',
            estimated_market_value: 9900,
            image: '//images.deadstock.co/products/sneakers/M9696/800xAUTO/IMG01.jpg',
            category: {
              name: 'sneakers'
            }
          }
        },
        {
          size: {
            size: '20',
          },
          packaging_condition: {
            name: 'Excellent',
          },
          product: {
            name: 'Converse All Star Ox Red',
            colorway: 'Red',
            sku: 'M9696',
            estimated_market_value: 9900,
            image: '//images.deadstock.co/products/sneakers/M9696/800xAUTO/IMG01.jpg',
            category: {
              name: 'sneakers'
            }
          }
        }]
      },
      {
        id: 12345678,
        quantity: 2,
        min_offer: null,
        price: 149875,
        created_at: '2023-04-05T07:56:33.000000Z',
        items: [{
          size: {
            size: '20',
          },
          packaging_condition: {
            name: 'Excellent',
          },
          product: {
            name: 'Converse All Star Ox Red',
            colorway: 'Red',
            sku: 'M9696',
            estimated_market_value: 9900,
            image: '//images.deadstock.co/products/sneakers/M9696/800xAUTO/IMG01.jpg',
            category: {
              name: 'sneakers'
            }
          }
        }]
      }]
    }
  },
}
</script>
