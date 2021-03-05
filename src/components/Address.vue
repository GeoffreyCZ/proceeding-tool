<template>
  <v-card>
    <v-card-title>
      {{ title }}
    </v-card-title>
    <v-card-text>
      <div v-if="allowSame">
        <v-checkbox
            label="Stejné jako trvalé"
            color="primary"
            v-model="isSame"
        ></v-checkbox>
      </div>
      <div v-if="!isSame">
        <v-text-field
            label="Ulice"
            outlined/>
        <v-text-field
            label="Číslo popisné / číslo orientační"
            outlined/>
        <v-text-field
            label="Město"
            outlined/>
        <v-text-field
            label="PSČ"
            outlined/>
      </div>
    </v-card-text>
  </v-card>
</template>

<script>
export default {
  name: "Address",
  props: {
    title: {
      type: String,
      default: 'Adresa'
    },
    allowSame: {
      type: Boolean,
      default: false
    }
  },
  data: () => ({
    isSame: false
  })
}
</script>

<style scoped>

</style>