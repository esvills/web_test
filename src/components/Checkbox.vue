<template>
    <label class="checkbox">
        <input type="checkbox" v-model="value" @change="$emit('input', $event.target.checked)" />
        <span class="checkmark"></span>
    </label>
</template>

<script>
export default {
  name: 'checkbox',
  props: {
    value: {
      type: Boolean
    }
  }
}
</script>
<style lang="sass" scoped>
    .checkbox
        display: inline-block
        position: relative
        margin-right: 25px
        width: 28px
        height: 28px
        border: 4px solid #d7d7d7
        border-radius: 8px
        vertical-align: middle

        input
            display: none

    .checkmark
        position: absolute
        width: 100%
        height: 100%
        background: url("../assets/cheked.png") no-repeat center
        opacity: 0

        .checkbox input:checked ~ &
            opacity: 1
</style>
