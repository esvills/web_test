<template>
  <div class="web__form--content_group">
      <div class="web__form--content_item web__form--shade">
          <checkbox v-model="item.checked" />
          <select class="input">
              <option :value="key" v-for="(sh,key) in $parent.shades" :key="key">{{ sh }}</option>
          </select>
      </div>
      <div class="web__form--content_item web__form--scope">
          <input class="input input--xs" value="1" v-model="item.scoped" /><span class="web__form--content_item--scope">Л</span>
      </div>
      <div class="web__form--content_item web__form--pack">
          <span class="web__form--content_item--pack">банка</span>
      </div>
      <div class="web__form--content_item web__form-func">
          <i class="icon icon-delete" @click.prevent="$parent.deleteItem(index)"></i>
      </div>
  </div>
</template>

<script>
import Checkbox from './Checkbox'
export default {
  name: 'item',
  props: {
    item: {
      type: Object
    },
    index: {
      type: Number,
      default: 0
    }
  },
  components: {
    Checkbox
  }
}
</script>
