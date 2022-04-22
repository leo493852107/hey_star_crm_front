<template>
  <div class="app-container">
    <el-table :data="list" border fit highlight-current-row style="width: 100%">

      <el-table-column align="center" label="ID" width="80">
        <template slot-scope="scope">
          <span>{{ scope.row.id }}</span>
        </template>
      </el-table-column>

      <el-table-column align="center" label="报价单" width="80">
        <template slot-scope="scope">
          <span>{{ scope.row.quote_no }}</span>
        </template>
      </el-table-column>

      <el-table-column align="center" label="名称" width="80">
        <template slot-scope="scope">
          <span>{{ scope.row.name }}</span>
        </template>
      </el-table-column>

      <el-table-column align="center" label="时间" width="80">
        <template slot-scope="scope">
          <span>{{ scope.row.quote_date }}</span>
        </template>
      </el-table-column>


    </el-table>

  </div>
</template>

<script>
import { fetchList } from '@/api/factory'
// import Pagination from '@/components/Pagination' // Secondary package based on el-pagination

export default {
  name: 'ArticleList',
  // components: { Pagination },
  // filters: {
  //   statusFilter(status) {
  //     const statusMap = {
  //       published: 'success',
  //       draft: 'info',
  //       deleted: 'danger'
  //     }
  //     return statusMap[status]
  //   }
  // },
  data() {
    return {
      list: [
        {
          'id': '1835c3ea-5094-46b4-ba6c-50a39dfbb7dc',
          'quote_no': 'FQ20220404TT',
          'name': null,
          'quote_date': '2022-04-04',
          'total_price': '0.00',
          'gross_margin': '1.20',
          'add_time': '2022-04-04T16:45:34.924231+08:00',
          'customer': '4d0f0dfe-e531-4db8-8713-9b371beeace3'
        },
        {
          'id': '22cc6e4f-6007-4f2d-b447-011cd846086a',
          'quote_no': 'FQ20220404AA',
          'name': '非常好 very good',
          'quote_date': '2022-04-05',
          'total_price': '0.00',
          'gross_margin': '2.20',
          'add_time': '2022-04-04T22:41:45.116514+08:00',
          'customer': '2d2a0128-f968-4141-b697-81b978b30ce7'
        }],
      listQuery: {
        page: 1,
        limit: 20
      }
    }
  },
  created() {
    this.getList()
  },
  methods: {
    getList() {
      fetchList(this.listQuery).then(response => {
        console.log(response.data)
        this.list = response.data.items
        this.total = response.data.total
        this.listLoading = false
      })
    }
  }
}
</script>

<style scoped>
.edit-input {
  padding-right: 100px;
}

.cancel-btn {
  position: absolute;
  right: 15px;
  top: 10px;
}
</style>
