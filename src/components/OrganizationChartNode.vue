<template>
  <table>
    <tbody>
    <tr>
      <td :colspan="datasource.children && datasource.children.length ? datasource.children.length*2 : null">
        <div v-if="datasource.children && datasource.children.length && datasource.Level > 0"
             @click.stop="handleExpand(datasource)">
          <slot name="expand" :expanded="expanded">
            pls
          </slot>
        </div>
        <div :class="{'node':true,['node-level-'+datasource.Level]:true}" :id="datasource.id" @click.stop="handleClick(datasource)">
          <slot :node-data="datasource">
            <div class="title">
              <i class="fa fa-users symbol"></i>
              {{ datasource.name }}
            </div>
            <div class="content">{{ datasource.title }}</div>
          </slot>
        </div>
      </td>
    </tr>
    <template v-if="datasource.children && datasource.children.length">
      <tr class="lines" v-bind:class="{'hidden': !expanded}">
        <td :colspan="datasource.children.length*2">
          <div class="downLine"></div>
        </td>
      </tr>
      <tr class="lines" v-bind:class="{'hidden': !expanded}">
        <td class="rightLine"></td>
        <template v-for="n in (datasource.children.length-1)">
          <td class="leftLine topLine"></td>
          <td class="rightLine topLine"></td>
        </template>
        <td class="leftLine"></td>
      </tr>
      <tr class="nodes" v-bind:class="{'hidden': !expanded}">
        <td colspan="2" v-for="child in datasource.children" :key="child.id">
          <node :datasource="child" :expanded-list="expandedList" :handle-click="handleClick"
                :handle-expand="handleExpand">
            <template v-for="slot in Object.keys($scopedSlots)" :slot="slot" slot-scope="scope">
              <slot :name="slot" v-bind="scope"/>
            </template>
          </node>
        </td>
      </tr>
    </template>
    </tbody>
  </table>
</template>

<script>
export default {
  name: 'node',
  props: {
    datasource: Object,
    expandedList: {
      default: () => {
        return {};
      },
      type: Object
    },
    handleExpand: Function,
    handleClick: Function
  },
  computed: {
    expanded() {
      return this.expandedList[this.datasource.Id+''] || this.datasource.Level === 0;
    }
  }
};
</script>

<style>
</style>
