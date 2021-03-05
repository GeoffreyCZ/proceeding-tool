<template>
  <div>
    <v-select
        v-model="proposer"
        :items="proposerOptions"
        label="Navrhovatel"
        outlined
    >
    </v-select>
    <Person title="Matka"/>
    <Person title="Otec"/>
    <div v-if="proposer === 'Jiná osoba'">
      <Person title="Navrhovatel"/>
    </div>
  </div>
</template>

<script>
import Person from "@/components/Person";

export default {
  name: "Determination",
  components: {Person},
  data: () => ({
    proposer: '',
    proposerOptions: ['Matka', 'Otec', 'Jiná osoba']
  })
}
</script>

<style scoped>

</style>