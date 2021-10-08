<template>
  <div class="table-wrapper">
    <h2>{{ title }}</h2>

    <div class="table-header">
      <div class="row header">
        <div class="column">
          <p>Идентификатор</p>
        </div>
        <div class="column">
          <p>Имя пользователя</p>
        </div>
      </div>
    </div>

    <div class="table-body">
      <div
        v-for="(row,indexRow) in dataTable"
        :key="indexRow"
        class="row"
        @click="rowClicked(row)"
      >
        <div v-for="(value,i) in row" :key="i" class="column">
          <p>{{value}}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'TableBody',
  props: {
    title: String,
    dataTable: Array
  },
  methods: {
    rowClicked (row) {
      this.$emit('rowClicked', row)
    }
  }
}
</script>

<style lang="scss">
h2 {
  color: #a1abcc;
}
.table-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.table-body {
  display: flex;
  flex-direction: column;
  .row:hover {
    background-color: #e5e5e5;
    cursor: pointer;
  }
}

.table-header {
  .row {
    background-color: #e5e5e5;
    cursor: default;
  }
}
.row {
  display: flex;
  width: fit-content;
}
.column {
  border: 1px solid;
  width: 300px;
  height: 50px;
  padding: 0 12px;
}
</style>
