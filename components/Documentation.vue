<template>
  <div id = "documentation" class = "proto_panel" v-bind:class = "{'expanded': expanded, 'collapsed': !expanded}">
    <!--
    <div class = "wrapper">

    <div class = "actionbar" v-if = "false">
      <input type = "text" v-model = "search" placeholder="type to filter..." />
    </div>

    <div class = "content" v-bind:class = "[view_type]">
      <div id = "browser" v-bind:class = "{hide_debug: !debug}">

        <div v-for = "object in queriedDocumentation" class = "object">
          <h3>{{object.name}}</h3>
          <ul>

            <li v-for = "f in object.fields"><p>{{f.name}}</p></li>
          </ul>
          <ul>

            <li v-if = "show_method(m)" v-for = "m in object.methods" v-bind:class = "{todo: m.status === 'TODO', todo_example: m.status === 'TODO_EXAMPLE', toreview: m.status === 'TOREVIEW', advanced: m.advanced === true, missing: m.status === 'missing'}">
              <p v-on:click = "select_method(object, m)">{{m.name}}()</p>
            </li>
          </ul>
        </div>
      </div>

      <transition name = "upanim" mode = "out-in">
        <div id = "card" v-if = "show_card">
          <documentation-card :data = "selected"></documentation-card>
        </div>
      </transition>

    </div>
  </div>
  -->

  </div>
</template>

<script>
import _ from 'lodash'
import DocumentationCard from './DocumentationCard'

export default {
  name: 'Documentation',
  components: {
    DocumentationCard
  },
  props: ['documentation'],
  data () {
    return {
      msg: 'Hello World!',
      debug: false,
      showing: true,
      selected: {},
      search: '',
      show_card: true,
      view_type: 'horizontal',
      expanded: true
    }
  },
  computed: {
    queriedDocumentation: function () {
      var that = this
      var doc = _.cloneDeep(this.documentation)

      if (!doc) return
      var k = doc.length
      while (k--) {
        doc[k].methods = doc[k].methods.filter(function (o) {
          if (o.name.toLowerCase().indexOf(that.search.toLowerCase()) !== -1) {
            return o
          }
        })

        doc[k].fields = doc[k].fields.filter(function (o) {
          if (o.name.toLowerCase().indexOf(that.search.toLowerCase()) !== -1) {
            return o
          }
        })

        if (doc[k].methods.length === 0) {
          doc.splice(k, 1)
          // console.log('remove ' + k)
        }
      }
      return doc
    }
  },
  methods: {
    show_method: function (m) {
      if (m.advanced) {
        // return this.sharedState.preferences['other']['show advanced api']
        return false
      } else {
        return true
      }
    },
    load_documentation: function (doc) {
      // this.documentation = store.state.documentation
      this.documentation = _.sortBy(doc, 'name')
      for (var k in this.documentation) {
        this.documentation[k].methods = _.sortBy(this.documentation[k].methods, 'name')
        this.documentation[k].fields = _.sortBy(this.documentation[k].fields, 'name')
      }
      // console.log('loaded ', this.documentation)
    },
    select_method: function (object, method) {
      var that = this
      this.show_card = false
      console.log('select_method')
      setTimeout(function () {
        console.log(object.name, method.name)
        that.show_card = true
        that.selected = { 'object': object, 'method': method }
      }, 20)
    },
    close: function () {
    },
    performSearch: function (objs) {
      var that = this
      console.log('qq', objs)
      return objs.filter(function (o) {
        return o.name.indexOf(that.search) !== -1
      })
    },
    switch_view: function () {
      switch (this.view_type) {
        case 'horizontal':
          this.view_type = 'vertical'
          break
        case 'vertical':
          this.view_type = 'over'
          break
        case 'over':
          this.view_type = 'horizontal'
          break
      }
    },
    close_card: function () {
      this.show_card = false
    }
  },
  created () {
  }
}
</script>

<style lang='less'>
@import (reference) "../assets/variables.less";

.header {
  h2 { color: @accentColor; }
  margin-bottom: 12px;
}

.todo {
  background: cyan;
}

.todo_example {
  background: yellow;
}

.toreview {
  background: purple;
}

.missing {
  background: orange;
}

.advanced::before {
  content: 'A';
  background: magenta;
}



.qq {
  max-height: 45px;
}
#documentation {
  height: 40%;
  background: white;
  display: flex;
  flex-direction: column;
  box-sizing: border-box;
  padding: 0px;
  z-index: 1;

  .actionbar {
    align-items: center;
    padding: 0;

    .title {
      width: 100%;
    }

    input {
      border: 0px;
      outline: none;
      padding: 8px;
      border-radius: 2px;
      background: transparent;
      width: 100%;
      font-size: 1em;
      box-sizing: border-box;
    }

    *::-webkit-input-placeholder {
      color: @primaryTextColor;
    }
    *:-moz-placeholder {
        /* FF 4-18 */
        color: @primaryTextColor;
    }
    *::-moz-placeholder {
        /* FF 19+ */
        color: @primaryTextColor;
    }
    *:-ms-input-placeholder {
        /* IE 10+ */
        color: @primaryTextColor;
    }
  }

  .wrapper {
    height: ~"calc(100vh - 398px)";
  }

  .content {
    background: white; /* #FFF3E0; */
    display: flex;
    height: 100%;
    min-height: 1px;
    padding: 0px;
    overflow: hidden;
    position: relative;

    &.horizontal {
      flex-direction: row;

      #browser {
      }
    }

    &.vertical {
      flex-direction: column;
    }


    &.over #card {
      position: absolute;
      width: 100%;
      height: 100%;
      box-sizing: border-box;
    }

    #browser {
      font-family: "Roboto Mono";
      flex: 2;
      overflow-y: scroll;
      overflow-x: hidden;

      &.hide_debug {
        ul li {
          background: transparent !important;

          &:before {
            content: '';
          }
        }
      }

      h1 {
        font-size: 1.1em;
        text-transform: uppercase;
        font-weight: 700;
      }

      h2 {
        font-size: 1.2em;
        font-weight: 600;
      }

      h3 {
        font-weight: 600;
        font-size: 0.8em;
        display: inherit;
        padding: 2px;
        color: black;
        margin-bottom: 6px;
        margin-left: 2px;
        border-radius: 0px;
      }


      .object {
        display: inline-block;
        vertical-align: top;
        width: 100%;
        margin-bottom: 10px;
        box-sizing: border-box;

        ul {
          column-count: auto;
          -moz-column-count: auto;
          column-gap: 25px;
          -moz-column-gap: 25px;
          column-width: 150px;
          -moz-column-width: 150px;
          font-size: 0.8em;
        }

        li {
          color: #333;
          font-weight: 400;

          p {
            cursor: pointer;
            padding: 4px;
            display: inline-block;
          }

          p:hover {
            background: @accentColor;
            color: white;
          }
        }
      }
    }
  }

  #card {
    padding: 0 18px;
    flex: 1.5;
    overflow: hidden;
    overflow-y: auto;
  }

}

</style>
