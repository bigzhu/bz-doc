

<template>
  <doc :name="name"
    :desc="desc"
    :parm_desc="parm_desc" 
    :parms="parms"
    :code="code"
    :call_back="call_back"
    ></doc>
</template>

<script>
  import 'bz-semantic-ui-site'
  import 'bz-semantic-ui-reset'
  import 'bz-semantic-ui-container'

  import 'bz-semantic-ui-table'
  import 'bz-semantic-ui-divider'

  // import 'semantic-ui/dist/components/site.css'
  // import 'semantic-ui/dist/components/reset.css'
  // import 'semantic-ui/dist/components/container.css'

  // import 'semantic-ui/dist/components/table.css'
  // import 'semantic-ui/dist/components/divider.css'

  // import 'semantic-ui/dist/components/button.css'
  // import 'semantic-ui/dist/components/icon.css'

  import Doc from './Bz.vue'
  export default {
    components: {
      Doc
    },
    data: function () {
      return {
        name: 'bz-doc',
        desc: '生成bz的doc',
        parm_desc: '没什么特别的，就是参数有点多',
        parms: [
          {parm: 'name', desc: '组件名'},
          {parm: 'desc', desc: '说明'},
          {parm: 'parm_desc', desc: '参数总说明'},
          {parm: 'parms', desc: '参数单个说明'},
          {parm: 'code', desc: '使用的代码'}
        ],
        code: `
    <doc :name="name"
    :desc="desc"
    :parm_desc="parm_desc" 
    :parms="parms"
    :code="code"
    :call_back="call_back"
    ></doc>`,
        oauths: [
          'vk',
          'douban',
          'youtube',
          'facebook',
          'google plus',
          'twitter',
          'github',
          'instagram'
        ]
      }
    },
    methods: {
    }
  }
</script>
<style lang=less>
</style>
