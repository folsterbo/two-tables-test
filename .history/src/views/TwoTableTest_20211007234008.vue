<template>
  <div class="home">
    <table-body
      title="Таблица 1"
      :dataTable="this.dataTableLocal"
      @rowClicked="updateTableLocal"
      >
    </table-body>
    <table-body
      title="Таблица 2"
      :dataTable="this.dataTableRemote"
      @rowClicked="updateTableRemote"
    >
    </table-body>
  </div>
</template>

<script>

import TableBody from '@/components/TableBody.vue'
import dataTableRemote from '../table.json'

export default {
  name: 'Home',
  components: {
    TableBody
  },
  data: function () {
    return {
      dataTableLocal: [
        {
          id: '1',
          name: 'Анна С.'
        },
        {
          id: '2',
          name: 'Петр К.'
        },
        {
          id: '3',
          name: 'Сергей Д.'
        }
      ],
      dataTableRemote
    }
  },
  methods: {
    updateTableLocal (data) {
      const indexLocal = this.dataTableLocal.indexOf(data)
      this.dataTableLocal.splice(indexLocal, 1)
      this.dataTableRemote.push(data)
    },
    updateTableRemote (data) {
      const indexRemote = this.dataTableRemote.indexOf(data)
      this.dataTableRemote.splice(indexRemote, 1)
      this.dataTableLocal.push(data)
    }
  }
}
</script>
