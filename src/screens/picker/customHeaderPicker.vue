
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
      <nb-body :style="{flex: 3}">
        <nb-title>Custom Header</nb-title>
      </nb-body>
      <nb-right />
    </nb-header>
    <nb-content>
      <nb-form>
        <nb-picker
          mode="dropdown"
          :render-header="getPickerHeaderComp"
          :ios-icon="getIosIcon()"
          header-back-button-text="Baaack!"
          :selected-value="selected1"
          :on-value-change="onValueChange"
        >
          <item
            label="Wallet"
            value="key0" />
          <item
            label="ATM Card"
            value="key1" />
          <item
            label="Debit Card"
            value="key2" />
          <item
            label="Credit Card"
            value="key3" />
          <item
            label="Net Banking"
            value="key4" />
        </nb-picker>
      </nb-form>
    </nb-content>
  </nb-container>
</template>

<script>
import {
  Picker,
  Icon,
  Header,
  Left,
  Button,
  Body,
  Title,
  Right
} from 'native-base'

export default {
  components: { Item: Picker.Item },
  data: function () {
    return {
      selected1: 'key1'
    }
  },
  methods: {
    onValueChange: function (value) {
      this.selected1 = value
    },
    getIosIcon: function () {
      return <Icon name="ios-arrow-down-outline" />
    },
    getPickerHeaderComp: function (backAction) {
      return (
        <Header style={{ backgroundColor: '#f44242' }}>
          <Left>
            <Button transparent onPress={backAction}>
              <Icon name="arrow-back" style={{ color: '#fff' }} />
            </Button>
          </Left>
          <Body style={{ flex: 3 }}>
            <Title>Your Header</Title>
          </Body>
          <Right />
        </Header>
      )
    }
  }
}
</script>

<style>
.body-icon-color {
  color: #999;
}
</style>
