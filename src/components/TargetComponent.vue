<template lang="pug">
  .target-component
    s-checkbox.target-component_button(v-model="hide" uid="button")
      span.far.fa-window-maximize
    target-list.target-component_list(v-show="!hide" :list="list" :change-list="changeList" :check-item="checkItem")
</template>

<script>
import TargetList from './TargetList.vue';
import SCheckbox from './SCheckbox.vue';

export default {
  components: {
    TargetList,
    SCheckbox,
  },
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
  data() {
    return {
      hide: true,
    }
  }
}
</script>

<style lang="sass">
.target-component
  position: relative
  &_button
    display: flex
    align-items: center
    justify-content: center
    width: 36px
    height: 36px
    border-radius: 4px
    box-shadow: 0px 7px 10px rgba(0, 0, 0, 0.22)
    &:hover
      outline: 1px solid #4cd946
  &_button .s-checkbox
    &_marker
      display: none
    &_label
      color: #c58b4a
      font-size: 21px
      line-height: 23px
      padding: 8px
      &:hover
        cursor: pointer
  &_list
    position: absolute
    top: 46px
</style>
