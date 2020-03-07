<template>
  <div class="component">
<<<<<<< HEAD
    <component v-if="componentName" :is="componentName" :config="config" :style="{color: info.fontColor}"></component>
=======
    <component v-if="componentName" :is="componentName" :config="config":style="{color: fontColor}"></component>
>>>>>>> ad9fad590195f423370b5c14351d770f2719a5f2
  </div>
</template>

<script type="text/ecmascript-6">
  import {VueExtend, Util} from 'godspen-lib'
  export default {
    mixins: [VueExtend.mixin],
    name: 'scroll-ranking',
    label: process.env.LABEL,
    style: process.env.STYLE,
    components: {},
    data () {
      return {
        componentName: ''
      }
    },
    props: {
      data: {
        type: Array,
        default () {
          return [
            {
              name: '周口',
              value: 55
            },
            {
              name: '南阳',
              value: 120
            },
            {
              name: '西峡',
              value: 78
            },
            {
              name: '驻马店',
              value: 66
            }
          ]
        },
        editor: {
          ignore: true
        }
      },
      info: {
        type: Object,
        default () {
          return {
            rowNum: 3,
            waitTime: 2000,
            carousel: 'single',
            unit: '',
            sort: true,
            fontColor: '#000'
          }
        },
        editor: {
          ignore: true
        }
      },
<<<<<<< HEAD
=======
      fontColor: {
        type: String,
        default: '#000',
        editor: {
          ignore: true
        }
      },
      sort: {
        type: Boolean,
        default: true,
        editor: {
          ignore: true
        }
      }
>>>>>>> ad9fad590195f423370b5c14351d770f2719a5f2
    },
    mounted: async function () {
      // 纯属演示异步加载js资源，与本组件无关； loadJs返回一个promise实例 可以用async 或者 then 来处理回调
      await Util.loadJs('https://unpkg.com/@jiaminghi/data-view@2.7.3/dist/datav.min.vue.js')
      setTimeout((e) => {
        this.componentName = 'DvScrollRankingBoard'
      }, 100)
    },
    computed: {
      config () {
        return {
          ...this.info,
          data: this.data,
<<<<<<< HEAD
=======
          rowNum: this.rowNum,
          waitTime: this.waitTime,
          carousel: this.carousel,
          fontColor: this.fontColor,
          unit: this.unit,
          sort: this.sort,
>>>>>>> ad9fad590195f423370b5c14351d770f2719a5f2
        }
      }
    },
    editorMethods: {
    },
    methods: {
    }
  }
</script>

<style lang="stylus" rel="stylesheet/stylus" type="text/stylus" scoped>
  .component {
    height: 100%;
    width: 100%;
  }
</style>
