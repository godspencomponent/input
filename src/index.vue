<template>
  <div class="component">
    <input class="component" :class="{'checkbox': type == 'checkbox' }" :type="type" :readonly='readonly' :maxlength='maxlength' :placeholder='placeholder' v-model='value'/>
  </div>
</template>

<script>
  import {VueExtend} from 'godspen-lib'

  export default {
    mixins: [VueExtend.mixin],
    name: 'input',
    label: process.env.LABEL,
    style: process.env.STYLE,
    props: {
      text: {
        type: [String, Number],
        default: '',
        editer: {
          type: 'text',
          label: '默认值',
        }
      },
      placeholder: {
        type: [String, Number],
        default: '请输入文本',
        editer: {
          type: 'text',
          label: '占位符',
          desc: '提示用户输入框的作用'
        }
      },
      type: {
        type: String,
        default: 'text',
        editer: {
          label: '类型',
          type: 'enum',
          defaultList: {
            text: '文本',
            tel: '数值',
            password: '密码',
            checkbox: '复选框'
          }
        }
      },
      readonly: {
        type: Boolean,
        default: false,
        editer: {
          label: '只读'
        }
      },
      maxlength: {
        type: Number,
        default: -1,
        editer: {
          label: '最大字符数'
        }
      }
    },
    data () {
      return {
        value: ''
      }
    },
    watch: {
      text () {
        this.value = this.scopeGet('text')
      }
    },
    computed: {
    },
    editerMethods: {
    },
    methods: {
      getValue () {
        return this.value
      },
      setValue (val) {
        this.value = val
      }
    }
  }
</script>

<style lang="stylus" rel="stylesheet/stylus" type="text/stylus" scoped>
  .component {
    width: 100%;
    height: 100%;
    outline: none;
    border: none;
    background: none;
    appearance none
    &.checkbox {
      width: auto;
      height: auto;
      appearance: checkbox;
    }
  }
</style>
