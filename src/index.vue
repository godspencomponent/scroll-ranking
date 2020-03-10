<template>
  <div class="component">
    <component
      v-if="componentName"
      :is="componentName"
      :config="config"
      :style="{color: info.fontColor}"
    ></component>
  </div>
</template>

<script type="text/ecmascript-6">
  import {VueExtend} from 'godspen-lib'
  import {
    scrollRankingBoard,
  } from '@jiaminghi/data-view'
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
      datasourcekey: {
        type: String,
        default: '',
        editor: {
          ignore: true
        }
      },
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
      }
    },
    mounted: async function () {
      // 纯属演示异步加载js资源，与本组件无关； loadJs返回一个promise实例 可以用async 或者 then 来处理回调
      window.Vue.use(scrollRankingBoard)
      this.componentName = 'DvScrollRankingBoard'
    },
    computed: {
      config () {
        var data = this.data
        if (this.datasourcekey) {
          var dataStr = this.dataHubGet && this.dataHubGet(this.datasourcekey)
          try {
            data = JSON.parse(dataStr)
          } catch (e) {
            console.log('error Scroll-Ranking', '获取数据解析json对象异常')
            data = []
          }
        }
        return {
          ...this.info,
          data: data,
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
