<template>
  <div id="app">
    <org-chart :datasource="ds" @node-click="selectNode">
<!--       <template slot-scope="{ nodeData }">
        <b @click="selectNode(nodeData)">{{ nodeData.name }}</b>
      </template> -->
    </org-chart>
  </div>
</template>

<script>
import OrgChart from './components/OrganizationChartContainer.vue'

export default {
  name: 'app',
  components: {
    OrgChart
  },
  data () {
    return {
      ds: {
        'Id': '1',
        'Level': 0,
        'name': 'Lao Lao',
        'title': 'general manager',
        'children': [
          { 'Id': '2','Level': 1, 'name': 'Bo Miao', 'title': 'department manager' },
          { 'Id': '3', 'Level': 1,'name': 'Su Miao', 'title': 'department manager',
            'children': [
              { 'Id': '4','Level': 2, 'name': 'Tie Hua', 'title': 'senior engineer' },
              { 'Id': '5', 'Level': 2,'name': 'Hei Hei', 'title': 'senior engineer',
                'children': [
                  { 'Id': '6','Level': 3, 'name': 'Pang Pang', 'title': 'engineer' },
                  { 'Id': '7', 'Level': 3,'name': 'Xiang Xiang', 'title': 'UE engineer' }
                ]
               }
             ]
           },
          { 'Id': '8', 'Level': 1,'name': 'Hong Miao', 'title': 'department manager' },
          { 'Id': '9', 'Level': 1,'name': 'Chun Miao', 'title': 'department manager' },
          { 'Id': '10','Level': 1, 'name': 'Bo 10', 'title': 'department manager' },
          { 'Id': '11','Level': 1, 'name': 'Bo 11', 'title': 'department manager' },
          { 'Id': '12','Level': 1, 'name': 'Bo 12', 'title': 'department manager' },
          { 'Id': '13','Level': 1, 'name': 'Bo 13', 'title': 'department manager' },
          { 'Id': '14','Level': 1, 'name': 'Bo 14', 'title': 'department manager' },
          { 'Id': '15','Level': 1, 'name': 'Bo 15', 'title': 'department manager' },
          { 'Id': '16','Level': 1, 'name': 'Bo 15', 'title': 'department manager' },
          { 'Id': '17','Level': 1, 'name': 'Bo 16', 'title': 'department manager' },
          { 'Id': '18','Level': 1, 'name': 'Bo 17', 'title': 'department manager' },
          { 'Id': '19','Level': 1, 'name': 'Bo 18', 'title': 'department manager' },
          { 'Id': '20','Level': 1, 'name': 'Bo 19', 'title': 'department manager' },
          { 'Id': '21','Level': 1, 'name': 'Bo 20', 'title': 'department manager' },
          { 'Id': '22','Level': 1, 'name': 'Bo 21', 'title': 'department manager' },
          { 'Id': '22','Level': 1, 'name': 'Bo 22', 'title': 'department manager' },
        ]
      }
    }
  },
  methods: {
    selectNode (nodeData) {
      alert('node ' + nodeData.name + ' is selected')
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
