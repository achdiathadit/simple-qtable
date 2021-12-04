<template>
    <div class="q-pa-md">
      <q-table
        title="Biodata"
        :rows="tableData"
        :columns="tableColumns"
        row-key="name"
        separator="vertical"
      />
      <!-- TODO: V-SLOT ERROR -->
      <!-- EXPANDABLE ROW -->
      <!-- <template v-slot:header="props">
        <q-tr :props="props">
          <q-th auto-width />
          <q-th
            v-for="col in props.cols"
            :key="col.name"
            :props="props"
          >
            {{ col.label }}
          </q-th>
        </q-tr>
      </template>
      <template v-slot:body="props">
        <q-tr :props="props">
          <q-td auto-width>
            <q-btn size="sm" color="accent" round dense @click="props.expand = !props.expand" :icon="props.expand ? 'remove' : 'add'" />
          </q-td>
          <q-td
            v-for="col in props.cols"
            :key="col.name"
            :props="props"
          >
            {{ col.value }}
          </q-td>
        </q-tr>
        <q-tr v-show="props.expand" :props="props">
          <q-td colspan="100%">
            <div class="text-left">This is expand slot for row above: {{ props.row.name }}.</div>
          </q-td>
        </q-tr>
    </template> -->
  </div>
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
        {
          name: 'action',
          label: 'Action',
          align: 'left',
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
