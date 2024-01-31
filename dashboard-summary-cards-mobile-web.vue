<template>
  <div class="container m-0 p-0" style="background-color: #F5F5F5">
    <div v-if="showWebStats" class="stats-web" @click="showWebStats = !showWebStats">
      <SummaryCardWeb icon="exchange-shoe-shirt" heading="Trade With Us..." subHeading="Have an item to trade?" subHeadingVariant="primary-500" information="Experience the Trade Arena and Trade your Footwear, Apparel, and Accessories today" buttonText1="Create a Listing" buttonLink1="/" buttonText2="Browse Trades" buttonLink2="/"  />
      <SummaryCardWeb icon="basket-with-shoe-hat" heading="Missed Some Items?" subHeading="Browse Our Selection" subHeadingVariant="primary-500" information="Check out our latest drops, exclusive streetwear, rare finds and more" buttonText1="Shop By Style" buttonLink1="/" buttonText2="Browse Shop" buttonLink2="/" />
      <SummaryCardWeb icon="trophy--with-ribbon" heading="Congratulations!" subHeading="You've Earned Points Today" subHeadingVariant="primary-500" information="Nice! You've earned a total of {-points-} for your purchase today" rewardPoints="400" buttonText1="View Rewards" buttonLink1="/" buttonText2="Keep Browsing" buttonLink2="/" />
    </div>
    <div v-else class="stats-mobile" @click="showWebStats = !showWebStats">
      <SummaryCardMobile icon="exchange-circle" heading="Trade With Us" anchorText="Browse Text" anchorVariant="primary" anchorLink="/" iconWidth="40px" iconHeight="40px" />
      <SummaryCardMobile icon="bag-filled" heading="Missing Items?" anchorText="Browse More" anchorVariant="primary" anchorLink="/" iconWidth="27px" iconHeight="27px" />
      <SummaryCardMobile icon="trophy-filled" heading="Congrats" rewardText="{-points-} Reward PTS" rewardPoints="400" subHeadingVariant="primary" information="Earned For Today's Trade" iconWidth="37px" iconHeight="41px" />
    </div>
  </div>
</template>

<script>
import SummaryCardMobile from '~/components/common-v2/Composites/SummaryCardMobile'
import SummaryCardWeb from '~/components/common-v2/Composites/SummaryCardWeb'
export default {
  name: 'Composite',
  components: {
    SummaryCardWeb,
    SummaryCardMobile,
  },
  data() {
    return {
      showWebStats: true
    }
  },
}
</script>
