<template>
    <div class="hello">
        <div class="web">
            <div class="web__left">
                <div class="web__header">
                    <h1>Выбраны {{ countCheckedList }} оттенка</h1>
                </div>
                <div class="web__form">

                    <div class="web__form--content">
                        <div class="web__form--content_item web__form--color">
                            <div class="web__form--header">Цвет</div>
                            <span class="web__form--content_item--color">Синий</span>
                        </div>
                        <div class="web__form--content_groups">
                            <div class="web__content--headers">
                                <div class="web__content--header web__form--shade">
                                    <checkbox @change='toggleSelect' v-model='isCheckAll'/>
                                    Оттенок
                                </div>
                                <div class="web__content--header web__form--scope">Объем</div>
                                <div class="web__content--header web__form--pack">Упаковка</div>
                                <div class="web__content--header web__form--func"><i @click.prevent="deleteAll"
                                                                                     class="icon icon-delete"></i></div>
                            </div>
                            <item :item="item" v-for="(item,index) in lists" :key="index" :id="index"></item>
                            <a href="#" class="web__button" @click.prevent="addShade">Добавить оттенок</a>
                        </div>
                    </div>
                </div>
            </div>
            <div class="web__right">
                <ul>
                    <li>
                        <a href="#">Состав заказа</a>
                    </li>
                    <li>
                        <a href="#">Комментарий</a>
                    </li>
                    <li>
                        <a href="#">Контактное лицо</a>
                    </li>
                </ul>
            </div>
        </div>
    </div>
</template>

<script>
import Item from './Item'
import Checkbox from './Checkbox'

export default {
  name: 'HelloWorld',
  data () {
    return {
      isCheckAll: false,
      shades: {
        0: 'Небесный',
        1: 'Голубой',
        2: 'Глубокий',
        3: 'Королевский'
      },
      lists: [
        {
          checked: false,
          shade: 0,
          scoped: 1
        },
        {
          checked: false,
          shade: 1,
          scoped: 1
        }
      ],
      msg: 'Welcome to Your Vue.js App'
    }
  },
  components: {
    Item,
    Checkbox
  },
  methods: {
    toggleSelect () {
      this.isCheckAll = !this.isCheckAll
      this.lists.forEach((item) => {
        item.checked = this.isCheckAll
      })
    },
    addShade () {
      this.lists.push(
        {
          checked: false,
          shade: 0,
          scoped: 1
        }
      )
    },
    deleteAll () {
      this.lists = []
    },
    deleteItem (key) {
      this.lists = this.lists.filter((e, k) => k !== key)
    }
  },
  computed: {
    countCheckedList () {
      return this.lists.filter((e) => e.checked).reduce((total) => total + 1, 0)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="sass">
a
    text-decoration: none
.icon
    display: inline-block
    background-repeat: no-repeat
    transition: opacity .5s ease
    cursor: pointer
    &:hover
        opacity: .5

    &-delete
        width: 24px
        height: 24px
        background-image: url("../assets/delete.png")

.hello
    width: 2000px

.input
    border: 4px solid #d7d7d7
    border-radius: 8px
    padding: 8px 16px
    width: 400px
    font-size: 32px
    display: inline-block
    text-align: center
    outline: none
    &--xs
        width: 67px
.web
    text-align: left
    display: flex
    &__left
        max-width: 1380px
        flex: 0 0 1380px
    &__right
        flex: 1
    &__button
        color: #e37458
        font-size: 32px
        border-bottom: 2px dotted
        position: relative
        padding-bottom: 2px
        margin-left: 159px
        margin-top: 24px
        display: inline-block
        &:before
            content: '+'
            position: absolute
            left: -20px

        &:hover
            color: darken(#e37458,20%)
    &__header
        padding: 35px 0 22px 0
        border-bottom: 6px solid #f1b16b
        margin-bottom: 30px
        h1
            margin: 0
            font-size: 48px
            padding-left: 65px
            font-weight: normal
    &__content
        &--headers
            display: flex
            margin-bottom: 53px
        &--header
            flex: 1
            font-size: 24px
            color: rgba(#000, .4)
    &__form
        &--color
            max-width: 405px
            flex: 0 0 405px
            padding-left: 65px
        &--shade
            flex: 0 0 514px
            max-width: 514px
        &--scope
            flex: 0 0 185px
            max-width: 185px
        &--pack
            flex: 0 0 180px
            max-width: 180px
        &--func
            flex: 0 0 25px
            max-width: 25px
        &--header
            font-size: 24px
            color: rgba(#000, .4)
            margin-bottom: 65px
            /*margin-left: 70px*/
        &--content
            padding: 25px 0 25px 0
            display: flex
            &_group
                display: flex
                align-items: center
            &_groups
                flex: 1
            &_item
                margin-bottom: 45px
                font-size: 24px

                &--scope
                    margin-left: 13px
                &--pack
                    font-size: 32px

                &--color
                    border-bottom: 2px solid rgba(#000, .15)
                    font-size: 36px
                    /*margin-left: 70px*/
</style>
