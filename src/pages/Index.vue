<template>
  <q-page class="flex flex-center">
    <div class="q-pa-md">
    <q-table
      title="Biodata"
      :rows="tableData"
      :columns="tableColumns"
      row-key="name"
    />
  </div>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'PageIndex',
  data () {
    return {
      tableColumns: [
        {
          name: 'name',
          label: 'Name',
          align: 'left',
          field: 'name',
          sortable: true
        },
        {
          name: 'age',
          label: 'Age',
          align: 'left',
          field: 'age',
          sortable: true
        },
        {
          name: 'hobbies',
          label: 'Hobbies',
          align: 'left',
          field: 'hobbies',
          sortable: true
        },
      ],
      tableData: []
    }
  },
  mounted () {
    this.getTableData()
  },
  methods: {
    getTableData () {
      this.$axios.get('http://demo2725834.mockable.io/api/v1/list').then((res) => {
          this.tableData = res.data.data;
          console.log(res.data.data);
        }).catch((err) => {
          console.error(err)
        })
    }
  }
})
</script>
