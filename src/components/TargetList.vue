<template lang="pug">
  div.target-list
    ul.target-list_list
      li.target-list_item(v-for="item in list" :key="item.id")
        s-checkbox.target-list_check(:uid="item.id" :value="item" v-model="checkedItems" @change="changeCheckedItems")
          span.target-list_text {{ item.text }}
        button.target-list_button(@click="removeItem(item)")
          span.fas.fa-minus
    div.target-list_control-panel
      button.target-list_control-button.target-list_control-button__refresh(@click="refreshList")
        span.fas.fa-redo
      button.target-list_control-button.target-list_control-button__add(@click="addItem")
        span.fas.fa-plus
</template>

<script>
import SCheckbox from './SCheckbox.vue';

export default {
  props: {
    list: {
      type: Array,
      required: true,
    },
    changeList: {
      type: Function,
      required: true,
    },
    checkItem: {
      type: Function,
      required: true,
    },
  },
  components: {
    SCheckbox,
  },
  data() {
    return {
      checkedItems: [],
    };
  },
  methods: {
    addItem() {
      let newList = [...this.list];
      let newItem = {id: '', text: ''};

      newItem.id = `${Date.now()}`;
      newItem.text = prompt('Text:');

      newList.push(newItem);
      this.changeList(newList);
    },
    removeItem(item) {
      let newList = [...this.list];
      newList.splice(newList.indexOf(item), 1);

      this.checkedItems.splice(this.checkedItems.indexOf(this.checkedItems.find((id) => id === item.id)), 1);
      this.changeList(newList);
      this.checkItem(this.checkedItems);
    },
    refreshList() {
      let newList = [];
      this.changeList(newList);
    },
    changeCheckedItems() {
      this.checkItem(this.checkedItems);
    },
  },
}
</script>

<style lang="sass">
.target-list
  display: flex
  flex-direction: column
  justify-content: space-between
  width: 276px
  height: 438px
  padding: 10px
  box-sizing: border-box
  border-radius: 4px
  background: #fff
  box-shadow: 0 7px 10px rgba(34, 34, 34, 0.22)
  &_list
    display: block
    margin: 0
    padding: 0  10px 0 0
    box-sizing: border-box
    margin: 0 0 10px 0
    overflow-y: scroll
    scrollbar-color: #e7e5dc transparent
    &::-webkit-scrollbar
      width: 10px
    &::-webkit-scrollbar-thumb
      background-color: #e7e5dc
      border-radius: 4px
    &::-webkit-scrollbar-track
      background-color: transparent
  &_item
    display: flex
    align-items: center
    justify-content: space-between
    padding: 8px 10px
    box-sizing: border-box
    border-radius: 4px
    margin: 0 0 6px 0
    background: #e7e5dc
    &:last-child
      margin: 0
  &_check
    width: 100%
  &_check .s-checkbox
    &_marker
      display: flex
      align-items: center
      justify-content: center
      width: 22px
      height: 22px
      padding: 6px
      border: 1px solid transparent
      border-radius: 4px
      background: #f5f4ed
      &__checked::after
        content: ''
        display: block
        flex-shrink: 0
        width: 10px
        height: 10px
        border-radius: 50%
        background: #4cd946
    &_label:hover
      cursor: pointer
    &_label:hover .s-checkbox_marker,
    &_input:active ~ .s-checkbox_marker,
    &_input:focus ~ .s-checkbox_marker
      border: 1px solid #4cd946
  &_text
    display: block
    margin: 0 auto
    font-family: Roboto, sans-serif
    font-style: normal
    font-weight: 300
    font-size: 12px
    line-height: 15px
    letter-spacing: 0px
    color: #38393b
  &_button
    display: flex
    justify-content: center
    align-items: center
    width: 15px
    height: 15px
    overflow: hidden
    padding: 0
    box-sizing: border-box
    margin: 0
    background: transparent
    border: none
    border-radius: 0
    outline: none
    font-size: 15px
    line-height: 23px
    text-decoration: none
    color: #38393b
    &:focus
      background: transparent
      outline: 1px solid #4cd946
      border: 1px solid black
    &:hover
      background: transparent
      outline: 1px solid #4cd946
      border: none
      cursor: pointer
    &:active
      background: transparent
      outline: 1px solid #4cd946
      border: none
    &:hover,
    &:focus,
    &:active
      outline: 1px solid #4cd946
      border: none
  &_control-panel
    flex-shrink: 0
    display: flex
    align-items: center
    justify-content: space-between
    box-sizing: border-box
    border-radius: 4px
    margin: 0 21px 0 auto
    background: #f5f4ed
  &_control-button
    display: flex
    justify-content: center
    align-items: center
    width: 36px
    height: 36px
    overflow: hidden
    padding: 8px
    box-sizing: border-box
    margin: 0 3px 0 0
    background: transparent
    border: none
    border-radius: 0
    outline: none
    font-size: 15px
    line-height: 23px
    text-decoration: none
    color: #38393b
    &:last-child
      margin: 0
    &:focus
      background: transparent
      outline: 1px solid #4cd946
      border: 1px solid black
    &:hover
      background: transparent
      outline: 1px solid #4cd946
      border: none
      cursor: pointer
    &:active
      background: transparent
      outline: 1px solid #4cd946
      border: none
    &:hover,
    &:focus,
    &:active
      outline: 1px solid #4cd946
      border: none
    &__refresh
      transform: rotateY(180deg)
</style>
