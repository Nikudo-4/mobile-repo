<template>
  <div>
      <div class="row items-center full-width" size="sm">
         <q-input rounded outlined
          v-model="search"
          placeholder="Поиск"
          @input="onSearchInput"
          @keyup.enter="onSearchInput"
        ></q-input>
        <!-- <q-space />
          <q-btn
            @click="onSearchInput"
            size="sm"
            variant="outline-primary"
          >
            <i class="material-icons">search</i>
          </q-btn> -->
      </div>
    

  </div>
</template>

<script>


export default {
  data() {
    return {
      search: ''
    }
  },

  methods: {
      onSearchInput(){
        this.$emit('input', this.search)
      },
      // onSearch(search){
      //     return FindOnPage(search)
      // }
  }
}
</script>
