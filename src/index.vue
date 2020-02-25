<template>
  <div class="component">
    <component v-if="componentName" :is="componentName" :config="config" style="width:320px;height:301px"></component>
  </div>
</template>

<script type="text/ecmascript-6">
  import {VueExtend, Util} from 'godspen-lib'
  // import  {scrollRankingBoard}  from '@jiaminghi/data-view'
  // import Vue from 'vue'
  // Vue.use(scrollRankingBoard)
  
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
      rowNum: {
        type: Number,
        default: 5,
        editor: {
          ignore: true
        }
      },
      waitTime: {
        type: Number,
        default: 2000,
        editor: {
          ignore: true
        }
      },
      carousel: {
        type: String,
        default: 'single',
        editor: {
          ignore: true
        }
      },
      unit: {
        type: String,
        default: '',
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
    },
    mounted: async function () {
      // 纯属演示异步加载js资源，与本组件无关； loadJs返回一个promise实例 可以用async 或者 then 来处理回调
      await Util.loadJs('https://unpkg.com/@jiaminghi/data-view@2.7.3/dist/datav.min.vue.js')
      setTimeout((e) => {
        this.componentName = 'DvScrollRankingBoard'
      }, 500)
    },
    computed: {
      config () {
        return {
          data: this.data,
          rowNum: this.rowNum,
          waitTime: this.waitTime,
          carousel: this.carousel,
          unit: this.unit,
          sort: this.sort,
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
    height 300px
    color: red;
    background-color #000
  }
</style>
