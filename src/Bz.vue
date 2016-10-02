<template>
  <div class="ui container segment">
    <h1>{{name}}</h1>
    <p>{{desc}}</p>
    <table class="ui celled table">
      <thead>
        <tr><th>参数</th><th>说明</th></tr>
      </thead>
      <tbody>
        <tr v-show="parm_desc">
          <td colspan="2" v-html="parm_desc"></td>
        </tr>
        <tr v-for="parm in parms"> <td class="single line"> {{parm.parm}} </td> <td> {{parm.desc}} </td></tr>
        <tr v-show="parms.length===0">
          <td colspan="2"></td>
        </tr>
      </tbody>
    </table>
    <code v-text="code"></code>
    <div class="ui divider"></div>
    <button v-show="call_back" @click='run' class='ui basic button'>
      <i class='icon play'></i>
      运行
    </button>
    <slot></solot>
  </div>
</template>

<script>
  import 'bz-semantic-ui-site'
  import 'bz-semantic-ui-reset'
  import 'bz-semantic-ui-container'

  import 'bz-semantic-ui-table'
  import 'bz-semantic-ui-divider'
  import 'bz-semantic-ui-button'
  import toastr from 'toastr'
  export default {
    props: {
      name: {
        type: String,
        required: true
      },
      desc: {
        type: String
      },
      parm_desc: {
        type: String
      },
      parms: {
        type: Array,
        default: []
      },
      code: {
        type: String
      },
      call_back: {
        type: Function
      }
    },
    components: {
    },
    data: function () {
      return {
      }
    },
    ready () {
      window.onerror = (message, source, lineno, colno, error) => {
        toastr.error(error.message)
        return false
      }
      window.addEventListener("unhandledrejection", function (event) {
          console.warn("WARNING: Unhandled promise rejection. Shame on you! Reason: "
            + event.reason);
      });
    },
    methods: {
      run: function () {
        if (this.call_back) {
          this.call_back()
        }
      }
    }
  }
</script>
<style>
  .original-text-bz {
    /*保留空格*/
    white-space: pre-wrap;
    /*字体能自动换行*/
    word-wrap:break-word;
  }
  code {
    padding: 2px 4px;
    font-size: 90%;
    color: #c7254e;
    background-color: #f9f2f4;
    border-radius: 4px;
    /*保留空格*/
    white-space: pre-wrap;
    /*字体能自动换行*/
    word-wrap:break-word;
  }
</style>
