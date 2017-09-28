<template>
  <div class="hello">
    <data-tables
       :data='tableData'
       :actions-def='getActionsDef()'
       :checkbox-filter-def='getCheckFilterDef()'
       :action-col-def='actionColDef'
       @row-click='itemClick()'
       :row-action-def='getRowActionsDef()'>
      <el-table-column prop="flow_no" label="No." sortable="custom">
      </el-table-column>
      <el-table-column prop="content" label="Content" sortable="custom">
      </el-table-column>
      <el-table-column prop="create_time" label="Time" sortable="custom">
      </el-table-column>
      <el-table-column prop="state" label="State" sortable="custom">
      </el-table-column>
      <el-table-column prop="flow_type" label="Type" sortable="custom">
      </el-table-column>
      <el-table-column prop="building_group" label="Building group" sortable="custom">
      </el-table-column>
      <el-table-column prop="building" label="building" sortable="custom">
      </el-table-column>
      <el-table-column prop="room_no" label="no" sortable="custom">
      </el-table-column>
      <el-table-column prop="cellphone" label="tel" sortable="custom" :width="500">
      </el-table-column>
    </data-tables>
  </div>
</template>

<script>
export default {
  name: 'hello',
  created () {
    this.tableData = [{
      'building': '5',
      'building_group': 'North',
      'cellphone': '13400000000',
      'content': 'Water flood',
      'create_time': '2016-10-01 22:25',
      'flow_no': 'FW201601010001',
      'flow_type': 'Repair',
      'flow_type_code': 'repair',
      'id': '111111',
      'room_id': '00501',
      'room_no': '501',
      'state': 'Created',
      'state_code': 'created'
    }, {
      'building': '6',
      'building_group': 'Sourth',
      'cellphone': '13400000000',
      'content': 'Lock broken',
      'create_time': '2016-10-01 22:25',
      'flow_no': 'FW201601010002',
      'flow_type': 'Repair',
      'flow_type_code': 'repair',
      'id': '2222222',
      'room_id': '00701',
      'room_no': '701',
      'state': 'Assigned',
      'state_code': 'assigned'
    }, {
      'building': '9',
      'building_group': 'North',
      'cellphone': '13400000000',
      'content': 'Help to buy some drinks',
      'create_time': '2016-10-02 22:25',
      'flow_no': 'FW201601010002',
      'flow_type': 'Help',
      'flow_type_code': 'help',
      'id': '2222222',
      'room_id': '00601',
      'room_no': '601',
      'state': 'Closed',
      'state_code': 'closed'
    }]
  },
  methods: {
    itemClick () {
      alert('a')
    },
    getActionsDef () {
      let self = this
      return {
        width: 5,
        def: [{
          name: 'new',
          handler () {
            self.$message('new clicked')
          },
          icon: 'plus'
        }, {
          name: 'import',
          handler () {
            self.$message('import clicked')
          },
          icon: 'upload'
        }]
      }
    },
    getCheckFilterDef () {
      return {
        width: 14,
        props: 'state_code',
        def: [{
          'code': 'created',
          'name': 'Created'
        }, {
          'code': 'assigned',
          'name': 'Assigned'
        }, {
          'code': 'accepted',
          'name': 'Accepted'
        }, {
          'code': 'closed',
          'name': 'Closed'
        }, {
          'code': 'cancelled',
          'name': 'Cancelled'
        }]
      }
    },
    getRowActionsDef () {
      let self = this
      return [{
        minWidth: '200',
        type: 'primary',
        handler (row) {
          self.$message('Edit clicked')
          console.log('Edit in row clicked', row)
        },
        name: 'Edit'
      }, {
        type: 'primary',
        handler (row) {
          self.$message('RUA in row clicked')
          console.log('RUA in row clicked', row)
        },
        name: 'RUA'
      }]
    }
  },
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      actionColDef: {
        label: 'test',
        def: [{
          handler: row => {
            this.$message('Edit clicked')
            console.log('Edit in row clicked', row)
          },
          name: 'Edit'
        }, {
          icon: 'message',
          type: 'text',
          handler: row => {
            this.$message('RUA in row clicked')
            console.log('RUA in row clicked', row)
          },
          name: 'RUA'
        }]
      },
      tableData: []
    }
  }
}
</script>
