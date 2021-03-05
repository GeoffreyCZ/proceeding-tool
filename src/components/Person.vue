<template>
  <v-card>
    <v-card-title>
      {{ title }}
    </v-card-title>
    <v-card-text>
      <v-text-field
          label="Jméno"
          outlined/>
      <v-text-field
          label="Příjmení"
          outlined/>
      <v-text-field
          label="Telefonní číslo"
          prepend-icon="mdi-phone"
          outlined/>
      <v-text-field
          label="E-mailová adresa"
          prepend-icon="mdi-at"
          outlined/>

      <v-menu
          ref="menu"
          v-model="menu"
          :close-on-content-click="false"
          transition="scale-transition"
          offset-y
          max-width="290px"
          min-width="auto"
      >
        <template v-slot:activator="{ on, attrs }">
          <v-text-field
              v-model="dateFormatted"
              label="Datum narození"
              persistent-hint
              prepend-icon="mdi-calendar"
              v-bind="attrs"
              @blur="date = parseDate(dateFormatted)"
              v-on="on"
          ></v-text-field>
        </template>
        <v-date-picker
            v-model="date"
            locale="cs-cz"
            :first-day-of-week="1"
            no-title
            @input="menu = false"
        ></v-date-picker>
      </v-menu>
      <Address title="Trvalé bydliště"/>
      <Address title="Faktické bydliště" allowSame="true"/>
    </v-card-text>
  </v-card>
</template>

<script>
import Address from "@/components/Address";

export default {
  name: "Person",
  components: {Address},
  props: {
    title: {
      type: String,
      default: '',
    },
  },
  data: vm => ({
    date: new Date().toISOString().substr(0, 10),
    dateFormatted: vm.formatDate(new Date().toISOString().substr(0, 10)),
    menu: false,
  }),

  watch: {
    date() {
      this.dateFormatted = this.formatDate(this.date)
    },
  },
  methods: {
    formatDate(date) {
      if (!date) return null

      const [year, month, day] = date.split('-')
      return `${day}.${month}.${year}`
    },
    parseDate(date) {
      if (!date) return null

      const [month, day, year] = date.split('/')
      return `${year}-${month.padStart(2, '0')}-${day.padStart(2, '0')}`
    },
  },
}
</script>

<style scoped>

</style>