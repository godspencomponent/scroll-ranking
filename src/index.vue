<template>
  <div class="component">
    <dv-scroll-ranking-board :config="config" style="width:320px;height:300px" />
  </div>
</template>

<script>
  import {VueExtend} from 'godspen-lib'

  export default {
    mixins: [VueExtend.mixin],
    name: 'scroll-ranking',
    label: process.env.LABEL,
    style: process.env.STYLE,
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
    color: red;
    background-color #000
  }
</style>
