<template>
  <nb-container :style="{ backgroundColor: '#fff' }">
    <nb-header>
      <nb-left>
        <nb-button
          transparent
          :on-press="() => this.props.navigation.goBack()"
        >
          <nb-icon name="arrow-back" />
        </nb-button>
      </nb-left>
      <nb-body>
        <nb-title>Advanced Deck Swiper</nb-title>
      </nb-body>
      <nb-right />
    </nb-header>
    <view :style="{flex: 1, padding: 12}">
      <nb-deck-swiper
        ref="_deckSwiper"
        :data-source="cardItemsArr"
        :looping="isLoopingRequired"
        :render-empty="handleCardEmpty"
        :render-item="handleCardRendering"
      />
    </view>
    <view :style="stylesObj.bottomBtnContainer">
      <nb-button
        icon-left
        :on-press="handleDeckSwiperBackBtn">
        <nb-icon name="arrow-back" />
        <nb-text>Swipe Left</nb-text>
      </nb-button>
      <nb-button
        icon-right
        :on-press="handleDeckSwiperForwardBtn">
        <nb-text>Swipe Right</nb-text>
        <nb-icon name="arrow-forward" />
      </nb-button>
    </View>
  </nb-container>
</template>

<script>
import { View, Text } from 'react-native'
import cardOne from '../../../../assets/swiper-1.png'
import cardTwo from '../../../../assets/swiper-2.png'
import cardThree from '../../../../assets/swiper-3.png'
import cardFour from '../../../../assets/swiper-4.png'

import CardComponent from '../common/card'

export default {
  data: function () {
    return {
      cardItemsArr: [
        {
          text: 'Card One',
          name: 'One',
          image: cardOne
        },
        {
          text: 'Card Two',
          name: 'Two',
          image: cardTwo
        },
        {
          text: 'Card Three',
          name: 'Three',
          image: cardThree
        },
        {
          text: 'Card Four',
          name: 'Four',
          image: cardFour
        }
      ],
      isLoopingRequired: false,
      stylesObj: {
        bottomBtnContainer: {
          flexDirection: 'row',
          flex: 1,
          position: 'absolute',
          bottom: 50,
          left: 0,
          right: 0,
          justifyContent: 'space-between',
          padding: 15
        }
      }
    }
  },
  methods: {
    handleCardEmpty: function () {
      return (
        <View>
          <Text>Over </Text>
        </View>
      )
    },
    handleCardRendering: function (item) {
      return <CardComponent item={item} />
    },
    handleDeckSwiperBackBtn: function () {
      this.$refs._deckSwiper._root.swipeLeft()
    },
    handleDeckSwiperForwardBtn: function () {
      this.$refs._deckSwiper._root.swipeRight()
    }
  }
}
</script>
